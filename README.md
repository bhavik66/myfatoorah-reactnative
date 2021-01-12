# myfatoorah-reactnative
# Introduction
MyFatoorah SDK v2, is an enhanced and improved SDK version that will simplify the integration with MyFatoorah payment platform through simple straight forward steps.


[# Prerequisites ](https://myfatoorah.readme.io/v2.0/docs/prerequisites-2)
In order to use MyFatoorah SDK on live environment, you have to consider some points to be done before you proceed with your live integration. Here you are the list that should be done and completed before going live with your account:

- You have to Create [ Live Account ](https://myfatoorah.readme.io/v2.0/docs/create-live-account) and get the account approved
- You have to get the API feature activated, you have to communicate with your account manager to enable it
- Get the API key that will be used within the integration
- If you are in need to have a [Direct Payment](https://myfatoorah.readme.io/v2.0/docs/direct-payment) integration working within your app, please communicate with your account manager to enable this feature for your as well

[![NPM](https://img.shields.io/npm/v/myfatoorah-reactnative.svg)](https://www.npmjs.com/package/myfatoorah-reactnative) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

# Demo Information
Demo account information

    baseURL: https://apitest.myfatoorah.com

    APIKey(Token): 7Fs7eBv21F5xAocdPvvJ-sCqEyNHq4cygJrQUFvFiWEexBUPs4AkeLQxH4pzsUrY3Rays7GVA6SojFCz2DMLXSJVqk8NG-plK-cZJetwWjgwLPub_9tQQohWLgJ0q2invJ5C5Imt2ket_-JAlBYLLcnqp_WmOfZkBEWuURsBVirpNQecvpedgeCx4VaFae4qWDI_uKRV1829KCBEH84u6LYUxh8W_BYqkzXJYt99OlHTXHegd91PLT-tawBwuIly46nwbAs5Nt7HFOozxkyPp8BW9URlQW1fE4R_40BXzEuVkzK3WAOdpR92IkV94K_rDZCPltGSvWXtqJbnCpUB6iUIn1V-Ki15FAwh_nsfSmt_NQZ3rQuvyQ9B3yLCQ1ZO_MGSYDYVO26dyXbElspKxQwuNRot9hi3FIbXylV3iN40-nCPH4YQzKjo5p_fuaKhvRh7H8oFjRXtPtLQQUIDxk-jMbOp7gXIsdz02DrCfQIihT4evZuWA6YShl6g8fnAqCy8qRBf_eLDnA9w-nBh4Bq53b1kdhnExz0CMyUjQ43UO3uhMkBomJTXbmfAAHP8dZZao6W8a34OktNQmPTbOHXrtxf6DS-oKOu3l79uX_ihbL8ELT40VjIW3MJeZ_-auCPOjpE3Ax4dzUkSDLCljitmzMagH2X8jN8-AYLl46KcfkBV

    API_Direct_Payment_Key(Token): TXLrkmSj-VlRTOOC2GCkpLbg2fWXIgcucpP6p0T94ZXcd3uqdg-YI7IUjCbaU1DsdsAGjIW3gnczqjv2CLFKfsiZ3GcD0H6zo5BxFCiAwK45lFGBDdmIw91QRPOtudpxuPJvdkjV_GVVyg5tfndVMc46CuSoNBqfLuzUWiSE51sy-EgboaIZHpFU8xl4fGRFzAwPprwFinftAq3cWTHDEb5dKcxrqIlVxpJM9gqdFo5S3-BsapiEBaVc69QEg2WXVSSf00giFXGiiCiXdD6LZQKn1iE3wQaJttbdDdNjPuLtH0KxNdqC24ONZEh6UKPDKWmOItbyDp-eA5lPJEsAo6BaLUQ5bcFQZXV7k0fk1Dnq4Wj0Rv9SmM7uyC58YFv6b2vxkcgbV1tu8D1bXPSgq7DlvpMn4mh-H1gBisp4xPjYzpfP91n3gvHuizUp4vd70VIuuGY1-cvOGeUs59RfrP4wk_X4UI_qjwNkVF0fS1Of02cIi4AFWNwGkT-ZZhz7Bg-9lyhrOQYrNiO1mIGgxv-OiG5Cc3y5arR7ZpSYl4K8A2TwQNCXZChoIdXwSDMYvHZTZHdmnNlTM2u7lXro9YDluR0vyE5rNacAI9ubEh-iCH7WeJF2xr32Pp_APn22BVyd-4gNpS5XUOIEK21xBxg2NAkuO2ukYC6CoyAAGeGRDBWOQjvm1gdzSjQ-AKrWNJiKwQ

[# Test Cards ](https://myfatoorah.readme.io/v2.0/docs/test-cards)


## Installation

```bash
npm install --save myfatoorah-reactnative
```

## Usage

## Requirments
To use `myfatoorah-reactnative` you should set your app in navigation container, so you need to install  `@react-navigation/native` and `@react-navigation/stack`

### 1- Install required depndecies (if your app already in navigaiton skip this step): 
 
```bash
$ npm install @react-navigation/native
```
- This depndecies are required for `@react-navigation/native`
```bash
$ npm install react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view
```
- If you are using Cocoapod you should do that:
```bash
$ cd ios && pod install
$ cd ..
.
.
$ npm install @react-navigation/stack
```

- `myfatoorah-reactnative` depends on `react-native-web` and `react-native-webview` depndecies so you should install them:
```bash 
npm install --save-dev react-native-web
npm install --save-dev react-native-webview
```

### 2- Setup your screen

```javascript
//Home.js
import React from 'react';
import {StyleSheet, Button, View } from 'react-native';
import {
  MFPaymentRequest,
  MFCustomerAddress,
  MFExecutePaymentRequest,
  Response,
  MFLanguage,
  MFMobileCountryCodeISO,
  MFCurrencyISO,
  MFPaymentype,
  MFKeyType
} from 'myfatoorah-reactnative';

export default function Home({ navigation })  {
    .
    .
    .
  onExecuteButtonClickHandler = () => {
    executePayment()
  };
  onExecuteDirectPaymentButtonClickHandler = () => {
    executeDirectPayment();
  };
  onGetPaymentStatusButtonClickHandler = () => {
    getPaymentStatus();
  };

  return (
      <View style={styles.container}>
        <Button title="Pay"
          onPress = {this.onExecuteButtonClickHandler}
        />
        <Button title="Direct Payment"
          onPress = {this.onExecuteDirectPaymentButtonClickHandler}
        />
        <Button title="Get Payment Status"
          onPress = {this.getPaymentStatus}
        />
      </View>
    );
}
}
```

```javascript
//App.js
import 'react-native-gesture-handler';
import * as React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import Home from 'path to Home.js'
import { MFWebView, MFSettings, MFTheme } from 'myfatoorah-reactnative';

const Stack = createStackNavigator();

export default class App extends React.Component {
  componentDidMount() {
    let baseURL = "https://apitest.myfatoorah.com";
    let token = "your token here";
    let theme = new MFTheme('blue', 'gray', 'Payment', 'Cancel')
    MFSettings.sharedInstance.setTheme(theme)
    MFSettings.sharedInstance.configure(baseURL, token);
  }

  render() {
    return (
      <NavigationContainer>
        <Stack.Navigator mode="modal" initialRouteName="Home">
          <Stack.Screen name="Home"
            component={Home} />
          <Stack.Screen name="MFWebView"
            component={MFWebView}
            options={MFWebView.navigationOptions}
          />
        </Stack.Navigator>
      </NavigationContainer>
    );
  }
}
```

### Execute Payment Service
```javascript
  //Home.js
  .
  .
  function executeResquestJson() {
    let request = new MFExecutePaymentRequest(parseFloat(invoiceValue), paymentMethods[selectedIndex].PaymentMethodId);
    request.customerEmail = "a@b.com"; // must be email
    request.customerMobile = "";
    request.customerCivilId = "";
    let address = new MFCustomerAddress("ddd", "sss", "sss", "sss", "sss");
    request.customerAddress = address;
    request.customerReference = "";
    request.language = "en";
    request.mobileCountryCode = MFMobileCountryCodeISO.KUWAIT;
    request.displayCurrencyIso = MFCurrencyISO.KUWAIT_KWD;
    // var productList = []
    // var product = new MFProduct("ABC", 1.887, 1)
    // productList.push(product)
    // request.invoiceItems = productList
    return request;
  }
  function executePayment() {
    let request = executeResquestJson();
    showLoading()
    MFPaymentRequest.sharedInstance.executePayment(navigation, request, MFLanguage.ENGLISH, (response: Response) => {
      hideLoading()
      if (response.getError()) {
        alert('error: ' + response.getError().error);
      }
      else {
        var bodyString = response.getBodyString();
        var invoiceId = response.getInvoiceId();
        var paymentStatusResponse = response.getBodyJson().Data;
        alert('success with Invoice Id: ' + invoiceId + ', Invoice status: ' + paymentStatusResponse.InvoiceStatus);
      }
    });
  }
```

### Execute Direct Payment Service
```javascript
  //Home.js
    .
    .
  function executeResquestJson() {
    let request = new MFExecutePaymentRequest(parseFloat(invoiceValue), paymentMethods[selectedIndex].PaymentMethodId);
    request.customerEmail = "a@b.com"; // must be email
    request.customerMobile = "";
    request.customerCivilId = "";
    let address = new MFCustomerAddress("ddd", "sss", "sss", "sss", "sss");
    request.customerAddress = address;
    request.customerReference = "";
    request.language = "en";
    request.mobileCountryCode = MFMobileCountryCodeISO.KUWAIT;
    request.displayCurrencyIso = MFCurrencyISO.KUWAIT_KWD;
    // var productList = []
    // var product = new MFProduct("ABC", 1.887, 1)
    // productList.push(product)
    // request.invoiceItems = productList
    return request;
  }
  function getCardInfo() {
    let cardExpiryMonth = '05'
    let cardExpiryYear = '21'
    let cardSecureCode = '100'
    let paymentType = MFPaymentype.CARD
    // let paymentType = MFPaymentype.TOKEN
    let saveToken = false
    let card = new MFCardInfo('5123450000000008', cardExpiryMonth, cardExpiryYear, cardSecureCode, paymentType, saveToken)
    card.bypass = true
    return card
  }
  function executeDirectPayment() {
    let request = executeResquestJson();
    let cardInfo = getCardInfo()
    showLoading()
    MFPaymentRequest.sharedInstance.executeDirectPayment(navigation, request, cardInfo, MFLanguage.ENGLISH, (response: Response) => {
      hideLoading()
      if (response.getError()) {
        alert('error: ' + response.getError().error)
      }
      else {
        // alert(response.getBodyString())
        var paymentStatusResponse = response.getBodyJson().getPaymentStatusResponse;
        var invoiceId = paymentStatusResponse.InvoiceId
        alert('success with Invoice Id: ' + invoiceId + ', Invoice status: ' + paymentStatusResponse.InvoiceStatus);
      }
    });
  }

```

### Get payment status
```javascript
  //Home.js
    .
    .
function getPaymentStatus() {
    var key = 'payment id or invoice id' 
    var keyType = MFKeyType.PAYMENTID // if key is payment id
    // var keyType = MFKeyType.INVOICEID // if key is invoice id
    var paymentStatusRequest = new MFPaymentStatusRequest(key, keyType);
    MFPaymentRequest.sharedInstance.getPaymentStatus(paymentStatusRequest, MFLanguage.ENGLISH, (response: Response) => {
      if (response.getError()) {
        alert('error: ' + response.getError().error)
      }
      else {
        alert(response.getBodyString())
        // var paymentStatusResponse = response.getBodyJson().getPaymentStatusResponse;
        // var invoiceId = paymentStatusResponse.InvoiceId
        // alert('success with Invoice Id: ' + invoiceId + ', Invoice status: ' + paymentStatusResponse.InvoiceStatus);
      }
    });
  }
```
### Apple Pay for iPhone devices.
## Apple Pay is available from iOS 13.0.
### Apple is like other payment getways but when creating execute payment request you should send payment id for Apply Pay.

Here you should set screen `MFWebView` in navigation to handle payment, and pass options as `options={MFWebView.navigationOptions}` to custom navigation bar, also you should pass `mode` as `mode="modal"` to present payment screen modally.

The demo has full details about all myfatoorah-reactnative funtions and how to use them, please check it.