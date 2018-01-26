[![web3swift: Elegant Blockchaining in Swift](https://raw.githubusercontent.com/web3swift/web3swift/master/web3swift.png)]
[![CocoaPods Compatible](https://img.shields.io/cocoapods/v/web3swift.svg)](https://img.shields.io/cocoapods/v/web3swift.svg)
[![Platform](https://img.shields.io/cocoapods/p/web3swift.svg?style=flat)](https://web3swift.github.io/web3swift)
[![Twitter](https://img.shields.io/badge/twitter-@mecruryprotocol-blue.svg?style=flat)](https://twitter.com/mercuryprotocol)

web3swift is a library written in Swift.

Table of contents
===

*  [Features](#features)
*  [Component Libraries](#component-libraries)
*  [Requirements](#requirements)
*  [Migration Guides](#migration-guides)
*  [Communication](#communication)
*  [Installation](#installation)
*  [Usage](Documentation/Usage.md)
    * **Intro -** [Creating Account](Documentation/Usage.md#making-a-request), [Encoding](Documentation/Usage.md#encoding)
*  [Improvements](#improvements)
*  [FAQ](#faq)
*  [Credits](#credits)
*  [Contributors](#contributors)
*  [License](#license)

## Features

- [x] Create Account
- [x] Import Account
- [x] Create and Encode Transaction
- [x] Sign Transaction
- [x] [Complete Documentation](https://web3swift.github.io/web3swift)

## Component Libraries

In order to keep web3swift focused specifically on core ethereum based utility functionality, additional component libraries will be created by the [Radical App LLC](https://github.com/web3swift/Foundation) to bring additional functionality to the mercury protocol ecosystem.

- [iOS Example App](https://git.cyberdust.com/sameer/web3SwiftExample.git) - Example showcasing use of web3swift library.
- [Mercury Wallet - Wallet App to use with mercury protocol. (Coming Soon)

## Requirements

- iOS 9.0+
- Xcode 9.2+
- Swift 4.0.0+

## Communication

- If you **need help**, use [Stack Overflow](http://stackoverflow.com/questions/tagged/web3swift). (Tag 'web3swift')
- If you'd like to **ask a general question**, use [Stack Overflow](http://stackoverflow.com/questions/tagged/web3swift).
- If you **found a bug**, open an issue.
- If you **have a feature request**, open an issue.
- If you **want to contribute**, submit a pull request.

## Installation

### CocoaPods

[CocoaPods](http://cocoapods.org) is a dependency manager for Cocoa projects. You can install it with the following command:

```bash
$ sudo gem install cocoapods
```

> CocoaPods 1.1+ is required to build web3swift 4.0+.

To integrate web3swift into your Xcode project using CocoaPods, specify it in your `Podfile`:

```ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '9.0'

target '<Your Target Name>' do
    use_frameworks!
    pod 'web3swift', '~> 0.0.6'
end
```

Then, run the following command:

```bash
$ pod install
```

## USAGE

### Create Account
Create keystore and account with password.
```bash
let configuration = EthAccountConfiguration(namespace: "wallet", password: "qwerty")
let (keystore, _) = EthAccountCoordinator.default.setup(configuration)
```
If you don't want to create account, this can be achieved by passing nil 
```bash
let configuration = EthAccountConfiguration(namespace: "wallet", password: nil)
let (keystore, _) = EthAccountCoordinator.default.setup(configuration)
```

### Encoding Transaction
```bash
var addressError: NSError? = nil
let amountToTransfer = 5
let gethToAccountAddress: GethAddress! = GethNewAddressFromHex("0x39db95b4f60bd75846c46df165d9e854b3cf1b56", &addressError)
guard let amount = GethBigInt.bigInt(amountToTransfer) else {
    print("Invalid amount")
    return
}
let transferFunction = EthFunction(name: "transfer", inputParameters: [toAccountAddress, amount])
let encodedTransferFunction = web3swift.encode(transferFunction)
```

### Signing Transaction
```bash
let signedTransaction = web3swift.sign(address: contractAddress, encodedFunctionData: encodedTransferFunction, nonce: nonce, gasLimit: Constants.gasLimit, gasPrice: Constants.gasPrice)
```


## FAQ

### What's web3swift?

web3swift is

## Credits

web3swift is owned and maintained by the [Radical App LLC](http://www.mercuryprotocol.com). You can follow them on Twitter at [@MercuryProtocol](https://twitter.com/mercuryprotocol) for project updates and releases.

## Contributors

* [Sameer Khavanekar](sameer@mercuryprotocol.com)
* [Rohit Kotian](rohit@mercuryprotocol.com)

If you do want to participate please follow the [guideline](CONTRIBUTING.md).

### Security Disclosure

If you believe you have identified a security vulnerability with web3swift, you should report it as soon as possible via email to security@mercuryprotocol.com. Please do not post it to a public issue tracker.

## License

web3swift is released under the MIT license. [See LICENSE](LICENSE) for details.
