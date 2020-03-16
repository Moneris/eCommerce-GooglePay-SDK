# Moneris® Google Pay™ SDK

Moneris® Google Pay™ SDK is a ready-to-install Android™ Library for developers who are integrating Google Pay™ with their Android™ devices. This will enable support for Google Pay™ on the merchant's payment app.  Google Pay™ gives your customers a faster, simpler way to pay - one where they don’t have to search for their wallets or fill in multiple payment forms.  The Moneris® Google Pay™ SDK provide features for merchants to easily link their Android™ application to their Moneris® merchant account.

## Getting Started

Follow the simple instructions below to enable add the Moneris® Google Pay™ SDK into your existing project

### Prerequisites

In order to integrate your Google Pay™ payment solution with Moneris®, there are a few basic tasks you need to do:

- Build an application using [Google Pay™ Android™ API](https://developers.google.com/pay/api/android/)
- Include the SDK listed in this repository or link the Moneris® Google Pay™ SDK into your project
- Customize your demo application code to work with Moneris® Gateway

### Linking using Gradle

#### Including the Moneris® Google Pay™ SDK Maven Repository
In the Project Gradle file

```Gradle
allprojects {
    repositories {
        google()
        jcenter()
    }
}
```
Add the additional maven repository stated below

```Gradle
allprojects {
    repositories {
        google()
        jcenter()
        maven {
            url "https://github.com/Moneris/eCommerce-GooglePay-SDK/raw/master"
        }
    }
}
```


#### Implementing Moneris® Google Pay™ SDK in the module
In the Module gradle where Google Pay™ is integrated
```Gradle
dependencies {
    implementation fileTree(include: ['*.jar'], dir: 'libs')
    implementation 'com.google.android.gms:play-services-wallet:16.0.0'    
}
```
Implement the googlepayapi as described below
```Gradle
dependencies {
    implementation fileTree(include: ['*.jar'], dir: 'libs')
    implementation 'com.google.android.gms:play-services-wallet:16.0.0'
    implementation 'com.moneris.googlepay:googlepayapi:1.2.0'
}
```
## Customizing your Google Pay™ Application for Moneris®

Modify the tokenizationSpecification object in the PaymentRequest with the **_gateway_** to **_moneris_** and the **_gatewayMerchantId_** to your moneris store id

Below is an example for linking your Google Pay™ application to process the merchant **_store5_**
```java
private static JSONObject getTokenizationSpecification() {
  JSONObject tokenizationSpecification = new JSONObject();
  tokenizationSpecification.put("type", "PAYMENT_GATEWAY");
  tokenizationSpecification.put(
      "parameters",
      new JSONObject()
          .put("gateway", "moneris")
          .put("gatewayMerchantId", "store5"));

  return tokenizationSpecification;
}
```
## Version Information

### Version 1.3.0

- Removed logging of requestXML for security
- Provided toXML() method in MonerisHttpsPost class to obtain request XML for debugging purpose

### Version 1.2.0

- Bug fix for GooglePay Preauth transaction

### Version 1.1.0

- Add INTERAC support for GooglePay

### Version 1.0.0

- Basic Google Pay™ Android™ Integration with Moneris® as the payment gateway.


