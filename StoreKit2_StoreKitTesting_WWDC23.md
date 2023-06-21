
---


### 1:42 - Create a listener for promoted in-app purchases

To create a listener for promoted in-app purchases, you can use the StoreKit framework in iOS. Here's an example of how to create a listener using the `PurchaseIntent` API:

```swift
import StoreKit

let promotedPurchasesListener = Task {
    for await promotion in PurchaseIntent.intents {
        // Process promotion
        let product = promotion.product

        // Purchase promoted product
        do {
            let result = try await product.purchase()
            // Process result
        }
        catch {
            // Handle error
        }
    }
}
```

Explanation:
- The code imports the StoreKit framework.
- A listener is created using `Task` and `await` to asynchronously listen for promoted in-app purchase intents.
- Inside the loop, each promotion is processed, and the associated product is obtained.
- The product is then purchased using the `purchase()` method, and the result is processed.
- Any errors that occur during the purchase process are caught and handled.

---


### 2:57 - Check promotion order

To check the current promotion order for in-app purchases, you can use the `Product.PromotionInfo.currentOrder` API from the StoreKit framework. Here's an example:

```swift
import StoreKit

do {
    let promotions = try await Product.PromotionInfo.currentOrder

    if promotions.isEmpty {
        // No local promotion order set
    }

    for promotion in promotions {
        let productID = promotion.productID
        let productVisibility = promotion.visibility
        // Check promoted products
    }
}
catch {
    // Handle error
}
```

Explanation:
- The code imports the StoreKit framework.
- The current promotion order is obtained using `Product.PromotionInfo.currentOrder` and stored in the `promotions` variable.
- If the `promotions` sequence is empty, it means no local promotion order is set for this device.
- The code then iterates over each promotion and retrieves the product ID and visibility.
- You can perform further operations or checks on the promoted products within the loop.
- Any errors that occur during the process are caught and handled.

---


### 3:26 - Set a promotion order

To set a custom promotion order for in-app purchases, you can use the `Product.PromotionInfo.updateProductOrder(byID:)` API from the StoreKit framework. Here's an example:

```swift
import StoreKit

let newPromotionOrder: [String] = [
    "acorns.individual",
    "nectar.cup",
    "sunflowerseeds.pile"
]

do {
    try await Product.PromotionInfo.updateProductOrder(byID: newPromotionOrder)
}
catch {
    // Handle error
}
```

Explanation:
- The code imports the StoreKit framework.
- A new promotion order is defined as an array of product identifiers in the desired order.
- The `updateProductOrder(byID:)` API is used to update the promotion order with the new order specified by `newPromotionOrder`.
- The changes are persisted locally on the device.
- Any errors that occur during the process are caught and handled.

---


### 4:02 - Update promotion visibility

To update the visibility of a promoted in-app purchase, you can use the `Product.PromotionInfo.updateProductVisibility(_:for:)` API from the StoreKit framework. Here's an example:

```swift
import StoreKit

// Hide “acorns.individual”
do {
    try await Product.PromotionInfo.updateProductVisibility(.hidden, for: "acorns.individual")
}
catch {
    // Handle error
}
```

Explanation:
- The code imports the StoreKit framework

.
- The `updateProductVisibility(_:for:)` API is used to update the visibility of a promoted in-app purchase.
- In this example, the visibility of the product with the identifier "acorns.individual" is set to `.hidden`, effectively hiding it from the promotion order.
- The changes are persisted locally on the device.
- Any errors that occur during the process are caught and handled.

---


### 4:17 - Update promotion visibility (alternative method)

To update the visibility of a promoted in-app purchase using an alternative method, you can modify the `visibility` property of a `PromotionInfo` object and call `update()` on the object to save the changes. Here's an example:

```swift
import StoreKit

do {
    let promotions = try await Product.PromotionInfo.currentOrder

    // Hide the first product
    if var firstPromotion = promotions.first {
        firstPromotion.visibility = .hidden
        try await firstPromotion.update()
    }
}
catch {
    // Handle error
}
```

Explanation:
- The code imports the StoreKit framework.
- The current promotion order is obtained using `Product.PromotionInfo.currentOrder` and stored in the `promotions` variable.
- The visibility of the first promoted product is updated by modifying the `visibility` property of the `firstPromotion` object.
- The changes are saved by calling the `update()` method on the `firstPromotion` object.
- The changes are persisted locally on the device.
- Any errors that occur during the process are caught and handled.

---


### 8:32 - Product view

To create a product view for a single in-app purchase using SwiftUI and StoreKit, you can use the `ProductView` component. Here's an example:

```swift
import SwiftUI
import StoreKit

struct BirdFoodShop: View {
    let productID: String
    let productImage: String

    var body: some View {
        ProductView(id: productID) {
            BirdFoodProductIcon(for: productID)
        }
        .productViewStyle(.large)
    }
}
```

Explanation:
- The code imports the SwiftUI and StoreKit frameworks.
- The `BirdFoodShop` struct represents a SwiftUI view for a bird food shop.
- The view displays a single in-app purchase product using the `ProductView` component.
- The `productID` and `productImage` variables are used to configure the `ProductView`.
- The `ProductView` is customized with the `BirdFoodProductIcon` view provided as a trailing closure.
- The style of the `ProductView` is set to `.large`.
- You can further customize the appearance and behavior of the product view to suit your needs.

---


### 8:52 - Store view

To create a store view displaying multiple in-app purchase products using SwiftUI and StoreKit, you can use the `StoreView` component. Here's an example:

```swift
import SwiftUI
import StoreKit

struct BirdFoodShop: View {
    let productIDs: [String]

    var body: some View {
        StoreView(ids: productIDs) { product in
            BirdFoodIcon(productID: product.id)
        }
    }
}
```

Explanation:
- The code imports the SwiftUI and StoreKit frameworks.
- The `BirdFoodShop` struct represents a SwiftUI view for a bird food shop.
- The view displays a store view with multiple in-app purchase products using the `StoreView` component.
- The `productIDs` array is used to specify the IDs of the products to be displayed.
- The `BirdFoodIcon` view is provided as a trailing closure to customize the appearance of each product.
- You can further customize the appearance and behavior of the store

 view to suit your needs.

---


### 9:19 - Subscription view

To create a subscription view using SwiftUI and StoreKit, you can use the `SubscriptionStoreView` component. Here's an example:

```swift
import SwiftUI
import StoreKit

struct BackyardBirdsPassShop: View {
    let groupID: String

    var body: some View {
        SubscriptionStoreView(groupID: groupID)
    }
}
```

Explanation:
- The code imports the SwiftUI and StoreKit frameworks.
- The `BackyardBirdsPassShop` struct represents a SwiftUI view for a subscription shop.
- The view displays a subscription store view using the `SubscriptionStoreView` component.
- The `groupID` variable is used to specify the subscription group ID.
- You can further customize the appearance and behavior of the subscription view to suit your needs.

---

### 21:09 - Simulated off-device purchase using StoreKitTest

To simulate an off-device purchase using StoreKitTest in an asynchronous context, you can use the `SKTestSession` and `buyProduct(identifier:options:)` methods. Here's an example:

```swift
import StoreKit
import StoreKitTest

func testSubscriptionRenewal() async throws {
    let session = try SKTestSession(configurationFileNamed: "Store")

    let oneYearInterval: TimeInterval = (365 * 24 * 60 * 60)
    let transaction = try await session.buyProduct(
        identifier: "birdpass.individual",
        options: [
            .purchaseDate(Date.now - oneYearInterval)
        ]
    )

    // Inspect transaction
}
```

Explanation:
- The code imports the StoreKit and StoreKitTest frameworks.
- The `testSubscriptionRenewal` function demonstrates an asynchronous test scenario using `async` and `await`.
- A new `SKTestSession` is created using a configuration file named "Store".
- The `buyProduct(identifier:options:)` method is used to simulate an off-device purchase.
- In this example, the product with the identifier "birdpass.individual" is purchased with a custom purchase date set to one year ago from the current date.
- The resulting transaction can be inspected or further processed within the test.

---

### 21:48 - Set a simulated purchase error when loading products

To simulate a purchase error when loading products using StoreKitTest, you can use the `SKTestSession` and `setSimulatedError(_:forAPI:)` methods. Here's an example:

```swift
import StoreKit
import StoreKitTest

func testLoadProducts() async throws {
    let session = try SKTestSession(configurationFileNamed: "Store")
    let productIDs = [
        "acorns.individual",
        "nectar.cup"
    ]

    // Set a simulated error, then load products, expecting an error
    session.setSimulatedError(.generic(.networkError), forAPI: .loadProducts)
    do {
        _ = try await Product.products(for: productIDs)
        XCTFail("Expected a network error")
    }
    catch StoreKitError.networkError(_) {
        // Expected error thrown, continue...
    }
    // Disable simulated error
    session.setSimulatedError(nil, forAPI: .loadProducts)
}
```

Explanation:
- The code imports the StoreKit and StoreKitTest frameworks.
- The `testLoadProducts` function demonstrates an asynchronous test scenario using `async` and `await`.
- A new `SKTestSession` is created using a configuration file named "Store".
- An array of product identifiers is defined in the `productIDs` variable.
- The `setSimulatedError(_:forAPI:)` method is used to simulate a network error for the `loadProducts
` API.
- The `products(for:)` method is called to load products, and an error is expected to be thrown.
- If the error is not thrown, a failure is recorded using `XCTFail`.
- If a `StoreKitError.networkError` is thrown, the test continues.
- Finally, the simulated error is disabled by setting it to `nil` for the `loadProducts` API.