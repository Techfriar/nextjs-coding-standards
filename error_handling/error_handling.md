## Error Handling in React

Error handling in React involves managing errors that occur during component rendering, data fetching, or event handling. React provides several mechanisms for handling errors effectively.


```javascript
 /**
   * function to edit Contact
   */
  const editContact = () => {
    setIsLoading(true);
    const selectedContactAssets = contactAsset.map(
      ({ asset_category_id, asset_id }) => ({
        asset_category_id,
        asset_id,
      })
    );
    void contactServices
      .editContact(
        contactId,
        firstName,
      )
      .then((response: ContactResponse) => {
        if (response.status) {
          AppToast.success({
            message: "Success",
            description: response.message,
          });
          setRefresh(!refresh);
          setContactEditOpen(false);
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
