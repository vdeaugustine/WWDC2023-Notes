# App Store's Tools for Testing In-App Purchases

## What are the tools offered by the App Store for testing in-app purchases?

The App Store provides three primary tools for testing in-app purchases:

- StoreKit Testing in Xcode: Allows for testing in-app purchases locally, without setting up products in App Store Connect.
- Sandbox: Uses products set up in App Store Connect for testing.
- TestFlight: Useful for end-to-end beta testing and gathering feedback from testers.

---


## What are the features of StoreKit Testing in Xcode?

StoreKit Testing in Xcode provides the following features:

- Allows testing of in-app purchases offline and in real-time, without a server.
- In-app purchases can be created and managed in the StoreKit configuration file.
- Enables testing of code changes locally.
- Simulations can be performed for advanced subscription use cases.
- Provides an ability to test subscription renewal rates.
- StoreKit errors can be simulated to build error handling in the app.
- It offers a Transaction Manager for managing multiple app instances and testing external transactions.

---


## What is the purpose of the App Store sandbox?

The App Store sandbox is used to test and validate the end-to-end implementation of in-app purchases on both the client and the server. It helps in building and qualifying the complete app experience.

Sandbox allows for validation of production-like scenarios such as purchases, restores, and subscription offers. It also allows for simulating scenarios around involuntary churn such as subscription billing problem messaging and billing grace period. Later this year, it will also provide support for testing Family Sharing for in-app purchases.

---


## How to test Family Sharing for in-app purchases in sandbox?

The following steps can be taken to test Family Sharing for in-app purchases in the sandbox:

1. Enable Family Sharing for the subscription or non-consumable products in App Store Connect.
2. Organize sandbox Family Sharing Members in App Store Connect.
3. Make a purchase with your sandbox Apple ID, which is enabled for Family Sharing.

Family Sharing in sandbox allows you to verify and validate use cases related to merchandising family-sharable products, entitling service to a family member, and revoking access to services.

---


## What are the new features to be added to the iOS sandbox Account Settings?

Later this year, new options to be added to the iOS sandbox Account Settings are:

- Adjusting subscription renewal rate.
- Testing interrupted purchases.
- Clearing purchase history.

---


## What is the purpose of TestFlight?

TestFlight is used for testing the app's end-to-end experience, distributing apps, and gathering feedback from a wider tester audience. It is used to validate and improve the app experience before releasing it on the App Store.

---


## How is managing testers in TestFlight made easier?

Management of testers in TestFlight is made easier through:

- Filtering by tester data like status and sessions.
- Bulk selection of testers to add or remove from a group.
- Using the 'Internal Only' method to distribute the build, ensuring it can be available to internal testers and cannot be submitted for App Store review.

---


## What are the common features of StoreKit Testing in Xcode, Sandbox, and TestFlight?

The common features of these tools include:

- Support for testing all types of in-app purchases.
- Accelerated rate of subscription renewals.

Different tools are used depending on the feature implementations, use cases, and organization's team structure.
