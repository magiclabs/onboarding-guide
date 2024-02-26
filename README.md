# Intro to Magic - Onboarding Guide
## Sections
- [Dashboard Walkthrough](#dashboard-walkthrough)
- [Enterprise Features](#enterprise-features)
- [Documentation Index](#documentation-index)
## Dashboard Walkthrough
- [Team Management](#team-management)
- [User Management](#user-management)
- [Authentication Settings](#authentication-settings)
- [Branding](#branding)
- [Widget UI](#widget-ui)
- [Security Settings](#security-settings)
---
### [TEAM MANAGEMENT](https://magic.link/docs/home/teams#managing-your-team)
#### ADD MEMBERS TO TEAM
- Invite collaborating team members
- Team members have access to all features **EXCEPT**
  - App deletion
  - View billing history
  - Update payment information
  <img width="1111" alt="teammanagement" src="https://github.com/magiclabs/onboarding-guide/assets/84942969/d5d84959-95e3-4cf3-95e4-7a48a98abfb0">
---
### USER MANAGEMENT
#### END USERS
- View user sign up date/time
- Search for users by email address, phone number or sub ID (if own IdP)
- [Disable MFA (if enabled and user activates)](#multi-factor-auth)
- [Download CSV with info of all users](https://magic.link/docs/authentication/features/data-export)
![users](https://github.com/magiclabs/onboarding-guide/assets/84942969/101abef3-ff88-436a-95d4-ec8cdcf9620b)
#### [EMAIL LOGS](https://magic.link/docs/authentication/features/email-logs)
- Event logs only available for email users
- Track unique users and conversion rates
- Search by email or IP address
- Use as a customer support tool
![emaillogs](https://github.com/magiclabs/onboarding-guide/assets/84942969/292effdc-ec30-409b-a3b0-9e111f6822c9)
---
### AUTHENTICATION SETTINGS
#### PASSWORDLESS LOGINS
- Email enabled by default
- SMS and WebAuthn must be enabled from dashboard before client SDK methods will work
![passwordlesslogins](https://github.com/magiclabs/onboarding-guide/assets/84942969/d764ebde-cc99-489f-a553-8ce94ea07f90)
#### [SOCIAL LOGINS](https://magic.link/docs/authentication/features/social-logins/oauth-implementation)
- Social login requires configuration with each provider
![sociallogins](https://github.com/magiclabs/onboarding-guide/assets/84942969/03033899-b4b6-432a-8fba-d3f28a53d784)
#### [MULTI-FACTOR AUTH](https://magic.link/docs/authentication/features/mfa)
- Enabling Mobile App MFA login gives user ability to set a 2nd factor on authentication through app on mobile device (i.e. Google Authenticator)
- The setting is triggered when app calls on the `showSettings` method on the [Web SDK User Module](https://magic.link/docs/api/client-side-sdks/web#user-module)
- End user's 2nd factor can be disabled by app owner in [USER section of dashboard](#user-management)
![mfa](https://github.com/magiclabs/onboarding-guide/assets/84942969/82e545d9-0abc-4c8a-9960-b045deb46fa3)
---
### BRANDING
#### MAGIC COMPONENTS
- Add brand logo, select primary color and theme
- Default email template (magic link and OTP)
- Magic UI when calling auth methods
- All Widget UI components
- Device registration UI
- User settings UI
![branding](https://github.com/magiclabs/onboarding-guide/assets/84942969/218a160b-84b2-48d2-911d-0a335130c469)
#### [CUSTOM EMAIL PROVIDER](https://magic.link/docs/authentication/customization/custom-smtp)
- When configured properly, users will receive login emails from custom email domain when logging in via email magic link or OTP
- Enabling this feature is a pre-requisite to [Custom Email Template](#custom-email-template)
![customemailprovider](https://github.com/magiclabs/onboarding-guide/assets/84942969/4574b8c2-3807-41ef-85a6-3ed22cf33e44)
---
### WIDGET UI
Available on 6 networks; Ethereum, Base, Polygon, Optimism, Arbitrum, and Flow
#### WALLET VIEW
- Default wallet view gives user token balance display and send/receive functionality
- Enabling NFT UI gives user ability to view token images
- Enabling NFT Transfer gives user ability to send token
- Enabling Fiat On-Ramps gives US users ability to purchase select token from providers
- Fiat On-Ramps for non-USA users require KYB with provider
#### SIGNATURE REQUEST UI
- Enabling Signature Request UI displays Magic UI on each signing operation
- UI displays transaction information for send transaction operations
- UI displays message information for personal sign operations
- When enabled, default behavior is for the Signature Request UI to render in same browser tab
- Signature Request UI can be displayed in pop-up tab under Magic's domain by enabling [Sign Confirmation security setting](#sign-confirmation)
![widgetui](https://github.com/magiclabs/onboarding-guide/assets/84942969/cbcff899-5c95-4a6b-b97a-f1a6a694f6a4)
---
### SECURITY SETTINGS
#### ALLOWED ORIGINS & REDIRECTS
- [Domain allowlist](https://magic.link/docs/authentication/security/allowlists/domain-allowlist) restricts which domains can use your Magic app publishable API key
- Domain allowlist is enabled by default and localhost cannot be removed
- Programmatic configuration of domain allowlist by API is possible
- [Allow redirect based auth flows for OAuth and/or email magic link with redirect](https://magic.link/docs/authentication/security/allowlists/redirect-allowlist)
- [Allow mobile apps to use Magic app publishable API key based on bundle ID (iOS) and/or package name (Android)](https://magic.link/docs/authentication/security/allowlists/mobile-access-allow-listing)
#### [CONTENT SECURITY POLICY](https://magic.link/docs/wallets/security/content-security-policy)
- Control which URLs are allowed by the browser's CSP when needing to load images or communicate with certain RPC URLs
#### [DEVICE REGISTRATION](https://magic.link/docs/authentication/security/device-registration)
- This security feature is disabled by default
- Enabling Device Registration will trigger additional security step (with Magic's UI/UX) during auth if browser/device is different from previous login
- While enabled, this feature will never trigger on a user's initial sign up
  ![allowlistcspndr](https://github.com/magiclabs/onboarding-guide/assets/84942969/0bb634cd-4312-4dfd-b553-1ab30db1d363)
#### [SIGN CONFIRMATION](https://magic.link/docs/wallets/security/sign-confirmation)
- Only relevant if [Signature Request UI is enabled in Widget UI section](#signature-request-ui)
- Enabling Sign Confirmation will display transaction information or sign message in a pop-up
#### [MAGIC LINK SECURITY CHECK](https://magic.link/docs/authentication/security/magic-link-security-check)
- Only relevant if using [email magic link method and **NOT** passing in a redirect URI](https://magic.link/docs/api/client-side-sdks/web#loginwithmagiclink)
- Enabling this while user logs in via email magic link method will present the user with a 3-digit OTP which needs to be submitted after clicking the emailed magic link
![signconfmagiclinkseccheck](https://github.com/magiclabs/onboarding-guide/assets/84942969/24b496ee-6019-45ff-bc60-8bd973a66d13)
#### [SESSION MANAGEMENT](https://magic.link/docs/authentication/security/session-management)
- Default session length is 7 days and persists session via third-party cookies
- Session length can be increased up to 90 days when Auto Refresh is enabled
- Enabling Auto Refresh persists session in first-party context through DPoP mechanism
#### [ACCESS CONTROL](https://magic.link/docs/authentication/security/access-control)
- Enabling Allow List is very restrictive, it **ONLY** allows those in that list to login via email auth methods or OAuth logins that have that email returned in scope
- Enabling Block List blocks users in that list from login via email auth methods or Oauth logins that have that email returned in scope
- Wildcarding is available on both lists
- Programmatic add and update to list by API is possible
![sessionmanagementaccesscontrol](https://github.com/magiclabs/onboarding-guide/assets/84942969/0ee91996-d2b7-4915-8bc5-e7d33a177120)
---
## Enterprise Features
The following features require an enterprise agreement and special enablement
- [Account Recovery](#account-recovery)
- [Custom Multi-Factor Authentication](#custom-multi-factor-authentication)
- [Generalized DKMS](#generalized-dkms)
- [Custom Email Template](#custom-email-template)
- [Account Linking](#account-linking)
- [Gas Subsidy](#gas-subsidy)
- [NFT Minting and Delivery](#nft-minting-and-delivery)
- [NFT Checkout](#nft-checkout)
### [ACCOUNT RECOVERY](https://magic.link/docs/authentication/enterprise-features/account-recovery)
- Only available for users who have logged in via email methods (`loginWithMagicLink` and `loginWithEmailOTP`)
- User can add phone number as recovery factor
### [CUSTOM MULTI-FACTOR AUTHENTICATION](https://magic.link/docs/authentication/enterprise-features/advanced-mfa)
- Integrate custom MFA provider to verify sessions
- When enabled, all logins must have issued JWT be set in the custom authorization header via Magic SDK method
### [GENERALIZED DKMS](https://magic.link/docs/wallets/enterprise-features/generalized-dkms)
- Leverage Magic's DKMS and allow user to encrypt any data with their PK
- Encrypted data is not stored by Magic
### [CUSTOM EMAIL TEMPLATE](https://magic.link/docs/authentication/enterprise-features/custom-email-template)
- [Custom Email Provider](#custom-email-provider) needs to be configured to use this feature
- Create one or multiple custom email templates for a single Magic app
![customemailtemplate](https://github.com/magiclabs/onboarding-guide/assets/84942969/5fc94f6b-0497-4810-b1bb-2163b4a10151)
### [ACCOUNT LINKING](https://magic.link/docs/authentication/enterprise-features/account-linking)
- Only available to Magic wallets and linking between users in the same Magic app
- Account linking via REST API sets a primary and secondary wallet and requires a user to login to both accounts
### [GAS SUBSIDY](https://magic.link/docs/wallets/enterprise-features/gas-subsidy)
- Only available on Polygon, smart contract must inherit ERC-2771 context
- Register smart contract and manage usage in Magic dashboard
- User must initiate transaction via Magic SDK gasless transaction method
![gassubsidy](https://github.com/magiclabs/onboarding-guide/assets/84942969/2247e817-95fb-405b-8760-1cb2c0c03fce)
### [NFT MINTING AND DELIVERY](https://magic.link/docs/nfts/features/minting-and-delivery)
- Only available on Polygon, smart contract must be ERC-721 or ERC-1155 and incorporate a minting function
- Register smart contract with Customer Success
- Call REST API endpoint to initiate mint and deliver (airdrop)
### [NFT CHECKOUT](https://magic.link/docs/nfts/features/checkout)
- Requires PayPal merchant account
- Enables fiat-based NFT primary sales purchases via Magic SDK NFT module method
---
## Documentation Index
### CLIENT-SIDE
#### WEB SDK
- [Getting started - import, construct and initialize magic](https://magic.link/docs/api/client-side-sdks/web#getting-started)
- Authentication Methods
  - [Auth Module - email and phone authentication methods](https://magic.link/docs/api/client-side-sdks/web#auth-module)
  - [OpenID Module - bring your own identity provider](https://magic.link/docs/api/client-side-sdks/web#open-id-module)
  - [OAuth Module - social provider login methods](https://magic.link/docs/api/client-side-sdks/web#o-auth-module)
  - [WebAuthn Module - biometric login methods](https://magic.link/docs/api/client-side-sdks/web#web-authn-module)
- [Wallet Module - widget UI methods](https://magic.link/docs/api/client-side-sdks/web#wallet-module)
- [NFT Module - NFT checkout and transfer methods](https://magic.link/docs/api/client-side-sdks/web#nft-module)
- [User Module - generate did token, get user metadata, check login status, display user settings and logout](https://magic.link/docs/api/client-side-sdks/web#user-module)
- [Response and Error Handling](https://magic.link/docs/api/client-side-sdks/web#response-and-error-handling)
#### REACT NATIVE SDK (BARE & EXPO)
- [Getting started - import, construct and initialize magic](https://magic.link/docs/api/client-side-sdks/react-native#getting-started)
- [Relayer - facilitates events between the Magic iframe context and the RN app](https://magic.link/docs/api/client-side-sdks/react-native#relayer)
- Authentication Methods
  - [Auth Module - email and phone authentication methods](https://magic.link/docs/api/client-side-sdks/react-native#auth-module)
  - [OpenID Module - bring your own identity provider](https://magic.link/docs/api/client-side-sdks/react-native#open-id-module)
  - [OAuth Module - social provider login methods](https://magic.link/docs/api/client-side-sdks/react-native#o-auth-module)
- [Wallet Module - widget UI methods](https://magic.link/docs/api/client-side-sdks/react-native#wallet-module)
- [NFT Module - NFT checkout and transfer methods](https://magic.link/docs/api/client-side-sdks/react-native#nft-module)
- [User Module - generate did token, get user metadata, check login status, display user settings and logout](https://magic.link/docs/api/client-side-sdks/react-native#user-module)
- [Response and Error Handling](https://magic.link/docs/api/client-side-sdks/react-native#response-and-error-handling)
#### FLUTTER SDK
- [Getting started - import, construct and initialize magic](https://magic.link/docs/api/client-side-sdks/flutter#getting-started)
- Authentication Methods
  - [Auth Module - email and phone authentication methods](https://magic.link/docs/api/client-side-sdks/flutter#auth-module)
  - [OpenID Module - bring your own identity provider](https://magic.link/docs/api/client-side-sdks/flutter#open-id-module)
  - [OAuth Module - social provider login methods](https://magic.link/docs/api/client-side-sdks/flutter#o-auth-module)
- [User Module - generate did token, get user metadata, check login status, display user settings and logout](https://magic.link/docs/api/client-side-sdks/flutter#user-module)
#### ANDROID SDK
- [Getting started - import, construct and initialize magic](https://magic.link/docs/api/client-side-sdks/android#getting-started)
- Authentication Methods
  - [Auth Module - email and phone authentication methods](https://magic.link/docs/api/client-side-sdks/android#auth-module)
  - [OpenID Module - bring your own identity provider](https://magic.link/docs/api/client-side-sdks/android#open-id-module)
- [Wallet Module - widget UI methods](https://magic.link/docs/api/client-side-sdks/android#wallet-module)
- [User Module - generate did token, get user metadata, check login status, display user settings and logout](https://magic.link/docs/api/client-side-sdks/android#user-module)
#### iOS SDK
- [Getting started - import, construct and initialize magic](https://magic.link/docs/api/client-side-sdks/ios#getting-started)
- Authentication Methods
  - [Auth Module - email and phone authentication methods](https://magic.link/docs/api/client-side-sdks/ios#auth-module)
  - [OpenID Module - bring your own identity provider](https://magic.link/docs/api/client-side-sdks/ios#open-id-module)
- [Wallet Module - widget UI methods](https://magic.link/docs/api/client-side-sdks/ios#wallet-module)
- [User Module - generate did token, get user metadata, check login status, display user settings and logout](https://magic.link/docs/api/client-side-sdks/ios#user-module)
- [Error Handling](https://magic.link/docs/api/client-side-sdks/ios#error-handling)
#### UNITY SDK
- [Getting started - import, construct and initialize magic](https://magic.link/docs/api/client-side-sdks/unity#getting-started)
- [Auth Module - email and phone authentication methods](https://magic.link/docs/api/client-side-sdks/unity#auth-module)
- [User Module - generate did token, get user metadata, check login status, display user settings and logout](https://magic.link/docs/api/client-side-sdks/unity#user-module)
#### BRING YOUR OWN IDENTITY PROVIDER
- [How to create and update your auth config](https://magic.link/docs/authentication/enterprise-features/idp)
### BLOCKCHAINS
- [Blockchain Integration](https://magic.link/docs/blockchains/overview)
### SERVER-SIDE
- [NodeJS SDK](https://magic.link/docs/api/server-side-sdks/node)
- [Python SDK](https://magic.link/docs/api/server-side-sdks/python)
- [Go SDK](https://magic.link/docs/api/server-side-sdks/go)
- [Ruby SDK](https://magic.link/docs/api/server-side-sdks/ruby)
- [PHP SDK](https://magic.link/docs/api/server-side-sdks/php)
- [Laravel SDK](https://magic.link/docs/api/server-side-sdks/laravel)
