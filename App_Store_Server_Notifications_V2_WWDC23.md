# App Store Server Notifications V2

**Q: What are App Store Server Notifications V2?**

App Store Server Notifications V2 is a feature by Apple that sends updates to your server about in-app purchases made in your app. This allows for minute-by-minute updates without needing to poll the App Store Server API.

- It covers a comprehensive set of events like subscription renewals, expirations, refunds, and more. 
- The events help track the full lifecycle of in-app purchases.
- The data comes in a familiar JSON format and is signed for authenticity assurance.
- They are compatible with apps that use StoreKit 2 or the original StoreKit API.

---


## New Updates and Features

**Q: What are the new updates to the App Store Server API and App Store Server Notifications V2?**

A collection of updates have been made to the App Store Server API and App Store Server Notifications V2. Some of these updates include:

1. **Transaction features:** New features have been introduced to make working with transactions on your server easier.
    - The new `Get Transaction Info` endpoint allows you to request the signed transaction information for a single purchase using just the transactionId. This includes even finished consumable transactions.
    - All transactionIds are supported irrespective of the product type or the finished status of the transaction.
    - Also, you can now call endpoints with any transactionId and not just the originalTransactionId.
    
2. **Enhancements to App Store Server Notifications:** There are enhancements that will help you reliably determine the status of your users' subscriptions.
    - A new status field is introduced to the data object of App Store Server Notifications V2. This indicates one of the five core states of a subscription.
    - It's included in every notification sent for auto-renewable subscriptions.
    - The Get Notification History endpoint allows you to request up to the last six months of version 2 notifications that were generated for your app.
    - The new request field `onlyFailures` in the Get Notification History endpoint returns only the notifications that have failed to reach your server.

3. **Migration away from older APIs:** Important updates about migrating away from older APIs have been made.
    - The verifyReceipt API and App Store Server Notifications V1 are considered deprecated and will no longer receive feature updates.
    - Migration to the newer APIs requires a few short steps detailed in the documentation.

---


## Migration from Older APIs

**Q: How to migrate from verifyReceipt API and App Store Server Notifications V1?**

The older APIs, verifyReceipt API and App Store Server Notifications V1, have been deprecated. Migration to the newer APIs includes:

- For **App Store Server API:**
  - Sign a JWT to represent your app and provide it as a header for every call to the API.
  - Save a transactionId for each of your users and provide it as a path parameter for calls to core endpoints.

- For **App Store Server Notifications V2:**
  - Prepare your server to parse the new V2 format.
  - Switch your preference from V1 to V2 notifications in App Store Connect.

- For testing, these newer APIs are available in the sandbox environment and the App Store Server Library has been released to assist with the migration process. It helps in calling the endpoints, verifying the signed data, and extracting transactionIds from receipts.
