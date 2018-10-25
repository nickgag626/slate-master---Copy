---
title: Ingenico mPOS SDK Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - java: Android



toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://www.ingenico.com/our-solutions/mobile-solutions'>Ingenico Mobile Solutions</a>

includes:
   - GettingStarted 
   - Setup
   - Initialize 

   
search: true
---

#Introduction


##What is the mPOS EMV SDK? 

The mPOS EMV SDK provides clients the ability to integrate with a wide range of Ingenico mobile card readers (as well as full integration with our EMV gateway) to begin seamlessly building an application and accepting mobile payments. 

By managing the end-to-end transaction (from card insertion to certified gateway processing), the SDK manages an application's compliance with all EMV certifications while eliminating PCI scope. Additionally, the SDK manages all communication required for an EMV transaction, simplifying the integration for developers. 

The mPOS EMV SDK isolates the transaction processing, reader management, reporting services and user management services from the user interface. This way, if an application needs to support new devices or backend processors, clients don’t have to rebuild their application from the ground-up. Instead, the Ingenico team will support remote software updates providing clients a future-proof solution to any changes in functionality, card readers or transaction types. 

The mPOS EMV SDK also supports integration with an existing application (for instance, if a client wishes to add payment processing as a new feature). The client can then easily begin accepting and processing credit card payments, including EMV contact, EMC contactless, and magnetic card-swipe transactions. 

The Ingenico EMV gateway is always improving, and is continually adding supported processors to the gateway to enhance functionality and marketability.

##What is included in the SDK?
* **A developer friendly toolkit**, including Android/iOS libraries, SDK documentation, sample code, and test applications;
* **A wide range of EMV-ready card readers**, with support for EMV chip & sign, EMV chip & PIN, NFC, and magstripe in a variety of form factors;
* **An EMV gateway**, with connections to all major processors in the U.S., thus offering ISVs and their customers the flexibility to use the processor of their choice, and
* **A future-proof solution**, offering the ability to easily upgrade to new Ingenico Mobile Solutions readers as they emerge or support additional processors without having to re-certify.

##Supported Readers
Once fully integrated with the SDK, customers will be able to seamlessly process payments using one of Ingenico’s many mobile card readers, which connect directly to a merchant’s mobile device. Ingenico offers a variety of card readers, giving customers the ability to choose one that best suits their needs without additional integration work. 
Customers will be able to accept EMV payments from any of the RP or MOBY series card readers, which include:

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
<br/>The Payment class provides APIs to accept credit / debit payments through Ingenico Mobile card readers, manually entered credit card payments as well as cash payments. These APIs include the business logic to drive a credit / debit transaction through Ingenico Mobile card readers and Ingenico gateway, hiding the different steps involved in processing a card payment..

**Payment Device Abstraction Layer**
<br/>The Payment Device class provides the APIs required to set up card readers for accepting payments, as well as retrieving all connection status updates.

**User**
<br/>The User class provides the APIs to perform different administrative actions (authentication, retrieve transactions history, details etc.,) against Ingenico backend services.


