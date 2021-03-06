Digiceipt is a web application aiming to support the conversion from paper receipt to digital receipt.

For deliverable 2, we have these three functionality to be testing:

The URL for our main page is:
http://digi--ceipt.herokuapp.com

1. User feature
   
   The user feature allows users to register their new account, login to user page, get all users to in order to find their ID, update user info and delete their user account.

  - Create account: 

    Routes: /insert-user

    Redirect to: /
	
    In order to create account, people needs to enter their username, password, first name and last name. These information will be stored into Users collection in Mongo DB. An _id attribute will be generated by mongoose to uniquely identify each user account.

  - User login:

    Routes: /user-login

    Redirect to: /userpage

    Test credential: 

      ID: 5ea410aee2e9a7ed17cd2857
      Username: Sibo123
      Password: 123
 
    To login their user accounts, users need to enter their id, username and password correctly. If the information they entered doesn't match to those stored in the database, the system will return a 403 error and users needs to click the "/" symbol to return to main page.

    Current limitation is that users can access user page directly by adding /userpage after the main page URL. This needs to be solved later in the development.

  - Get all users:

    Routes: /get-user

    This feature will return an item object containing all user documents to main page and display the information for all user accounts.

    This feature aims to help users find their unique id.

  - Update information:

    Routes: /update-user-info

    Redirect to: /

    This feature allows users to update their information by entering their unique id and information they want to be set. In future, this feature will have an authentication feature to check users old password and new password.

    
  - Delete users:

    Routes: /delete-user

    Redirect to: /
    
    This feature allows users to delete their user account by entering the unique id for their account. In future, this feature needs to have an authentication feature to prevent users delete other users account.
    

2. Receipt feature

   The receipt feature allows users to create a receipt under a user account, list all receipts and delete receipt by ID.

   - Create receipt:

     Routes: /create-receipt

     Redirect to: /userpage

     To create a receipt, a user needs to input their receipt's information, including shop name, description, price and buyerID. BuyerID should be the ID of the users account for this receipt. 

     This function will bind this receipt to the user document with the same _id as buyerID.

   - List all receipts:

     Routes: /get-receipt

     This feature will return an item object containing all receipt documents in Receipt collection to user page and display the information for all receipts.

     This feature aims to help users find their _id. But this function will be discarded in the future because people should not have access to all receipts in the database.

   - delete receipts:

     Routes: /delete-receipt

     This feature allows users to delete a receipt with the same id as their input id. In the future, this feature will only allow user to delete receipts under their user account.

3. List all receipts for a user

   This feature added the relationship between Receipt collection and User collection and allows users to find all receipts for a user id.

   - List all receipts for a user feature:

   Routes: /list-user-receipt

   This feature allows users to display all receipts under a user account by entering their user id. In the future, this function will not need user to input their id and display receipts under their user account only.ss