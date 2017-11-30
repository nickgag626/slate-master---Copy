---
title: Ingenico mPOS SDK Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - java: Android
  - swift: iOS
  - csharp: Windows



toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://www.ingenico.com/our-solutions/mobile-solutions'>Ingenico Mobile Solutions</a>

includes:
   - GettingStarted 
   - Setup
   - Initialize 
   - ManualCardEntry 
   - CashTransaction
   - SettingEnvironment
   - BuildCredit

   
search: true
---

#Introduction


##What is the mPOS EMV SDK?

The mPOS EMV SDK provides integration with a range of Ingenico mPOS card readers, as well as full integration with our EMV Gateway. By managing the end-to-end transaction (from card insertion to certified gateway processing), the SDK employs a semi-integrated approach keeping the mobile application compliant with all EMV certifications while eliminating PCI scope. Additionally, the SDK manages the lower-level back and forth communication required for an EMV transaction, simplifying the integration for developers. The mPOS EMV SDK isolates the transaction processing, reader management, reporting services and user management services from the UI. This way, if an application needs to support new devices or backend processors, clients don’t have to rebuild their application from the ground-up. Updates to the SDK will provide the client with components to support any future changes in functionality, such as adding additional mPOS card readers or supporting new transaction types.

Our EMV gateway is always improving, and we are continually adding supported processors to our gateway to enhance our functionality and marketability.

The integration of the mPOS EMV SDK with an existing application allows an end-user to easily accept and process credit card payments, including EMV Contact, EMV Contactless and Magnetic Card Swipe transactions.


##What is included in the SDK?
* **A developer friendly toolkit**, including Android/iOS libraries, SDK documentation, sample code, and test applications;
* **A wide range of EMV-ready card readers**, with support for EMV chip & sign, EMV chip & PIN, NFC, and magstripe in a variety of form factors;
* **An EMV gateway**, with connections to all major processors in the U.S., thus offering ISVs and their customers the flexibility to use the processor of their choice; and
* **A future-proof solution**, offering the ability to easily upgrade to new Ingenico Mobile Solutions readers as they emerge or support additional processors without having to re-certify.

##Supported Readers
Once fully integrated with the SDK, customers will be able to seamlessly process payments using one of Ingenico’s many mobile card readers, which connect directly to a merchant’s mobile device. Ingenico offers a variety of card readers, giving customers the ability to choose one that best suits their needs without additional integration work. 
Customers will be able to accept EMV payments from any of the RP-reader series, which includes:

Reader | Payment Type Accepted | Supported Communication Interfaces
--------- | ------- | -----------
RP350 |EMV Chip & Sign, MSR Mobile Card Reader | Audio Jack 
RP450 | SR NFC, EMV NFC, EMV Chip & Sign, MSR Mobile Card Reader | Bluetooth, Audio Jack
RP750 | MSR NFC, MSR EMV, EMV Chip & Pin, PIN Debit | Bluetiith, Audio Jack
MOBY/3000 | MSR MSR EMV, EMV Chip & Pin, PIN Debit, MSR Mobile Card Reader | Bluetooth, (USB for Android only)
MOBY/8500 | MSR NFC, MSR EMV, EMV Chip & Pin, PIN Debit | Bluetooth

##Breakdown of the Ingenico mPOS EMV SDK

The Ingenico mPOS EMV SDK includes four components:

**Ingenico** 
<br/>The Ingenico class serves as the entry-point to the mPOS SDK. The APIs included will aid in initializing the project, as well as return the necessary information needed to begin processing transactions and managing devices. 

**Payment** 
<br/>Payment provides APIs to accept credit / debit payments through Ingenico Mobile card readers, manually entered credit card payments as well as cash payments. These APIs include the business logic to drive a credit / debit transaction through Ingenico Mobile card readers and Ingenico gateway, hiding the different steps involved in processing a card payment..

**Payment Device Abstraction Layer**
<br/>Payment Device provides the APIs required to setup card readers to be used for accepting payments, as well as retrieve all connection status updates.

**User**
<br/>User provides the APIs to perform different administrative actions (authentication, retrieve Transactions history, details etc.,) against MCM backend services.


