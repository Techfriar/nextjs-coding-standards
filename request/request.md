## Handling Requests

```javascript
const createContacts = () => {
  setIsLoading(true);
  const selectedContactAssets = contactAsset.map(
    ({ asset_category_id, asset_id }) => ({
      asset_category_id,
      asset_id,
    })
  );
  void contactServices
    .createContact(
      firstName,
      lastName,
      phoneNumber,
      dialCode,
      uniCode,
      email,
      company,
      jobTitle,
      service,
      assetTypeAttribute,
      serviceTerritory,
      street,
      city,
      state,
      zipCode || undefined,
      country,
      addNotes,
      selectedContactAssets,
      file
    )
    .then((response: ContactResponse) => {
      if (response.status) {
        AppToast.success({
          message: "Success",
          description: response.message,
        });
        setContactAddOpen(false);
        setDefultErrorMessage("");
      } else if (response.errors) {
        setDefultErrorMessage("Error!...Please check the fields");
        const errorMessage: Record<string, string> = response.errors;
        [errorMessage].map((item) => {
          if (item.first_name) {
            setFirstNameError(item.first_name);
          }
          if (item.phone) {
            setPhoneNumberError(item.phone);
          }
          if (item.email) {
            setEmailError(item.email);
          }
          if (item.zip_code) {
            setZipCodeError(item.zip_code);
          }
        });
      } else {
        AppToast.error({
          message: "Error",
          description: response.message,
        });
      }
      setIsLoading(false);
    });
};

export default function useContactService() {
  /**
   * Method to add contact
   * @return Promise<ContactResponse>
   */
  const createContact = async function (
    firstName?: string,
    lastName?: string,
    phone?: string,
    countryCode?: string,
    uniCode?: string,
    email?: string,
    company?: string,
    jobTitle?: string,
    service?: string[],
    assetTypeAttribute?: string[],
    serviceTerritory?: string[],
    street?: string,
    city?: string,
    state?: string,
    zipCode?: string,
    country?: string,
    notes?: string,
    assets?: ContactAssets[],
    file?: File
  ): Promise<ContactResponse> {
    const props: JSON = <JSON>(<unknown>{
      first_name: firstName ?? "",
      last_name: lastName,
      phone: phone,
      country_code: countryCode,
      country_unicode: uniCode,
      email: email,
      company: company,
      job_title: jobTitle,
      services: service,
      asset_types: assetTypeAttribute,
      service_territories: serviceTerritory,
      street: street,
      city: city,
      state: state,
      zip_code: zipCode,
      country: country,
      note: notes,
      assets: assets,
      profile_picture: file,
    });

    try {
      const { body } = await http().post("api/contact/add", props, true);

      const response: ContactResponse = {
        status: body.status,
        message: body.message,
        errors: body.errors,
      };
      return response;
    } catch (error) {
      return {
        status: false,
        message: "Failed to add contact...Try again!",
      };
    }
  };
}
