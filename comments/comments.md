```javascript

>Inline Comments
 //update the errors in the add focus area modal
  const updateCharityErrors = (errorObject: NewCharityErrorsType): void => {
    setCharityErrors((prevErrors: NewCharityErrorsType) => {
      // Create a copy of the previous state
      const newErrors: NewCharityErrorsType = { ...prevErrors };

      // Iterate over the keys of the errorObject
      Object.keys(errorObject).forEach((key) => {
        // Update the corresponding key in the newErrors object
        newErrors[key as keyof NewCharityErrorsType] =
          errorObject[key as keyof NewCharityErrorsType];
      });

      // Return the updated state
      return newErrors;
    });
  };


 /**
   * Method for add new charity
   * @param CharityType
   * @return Promise<addCharityType>
   */
  const addCharity = async function (
    newCharity: CharityType | undefined
  ): Promise<addCharityResponse> {
    const props: JSON = <JSON>(<unknown>{
      category_id: newCharity?.category_id,
      currency_id: newCharity?.currency_id?.toString(),
      country_id: newCharity?.country_id?.toString(),
      name: newCharity?.name,
      website: newCharity?.website,
    });
    try {
      const { body } = await http().post(
        "/api/philanthropy/charity/add",
        props,
        false
      );

      const response: addCharityResponse = {
        status: body.status,
        message: body.message,
        errors: body.errors,
        charity: body.data ? body.data : undefined,
      };
      return response;
    } catch (error) {
      return {
        status: false,
        message: "Failed to add new focus area...Try again!",
      };
    }
  };
