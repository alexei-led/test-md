## Plain Test Case - Run (2014-11-04T10:15:16Z)

This is how Test Set run will look like. Title contains an original Test Case name plus Run and also a timestamp in ISO 8601 format. Quote under description contains duration according to above format
> PT10M45S
> @alexei

- This is executed step
- Verify that everything is OK
  > :+1: The validation passed
- ~~Non executed step~~
- Doing this step, produces unexpected Error
  > :x: Error - everything crashed! Help!
- Verify something that always fail
  > :-1: Fail - Hmm... the validation fails indeed!
