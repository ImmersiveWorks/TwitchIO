### Version 1.2.0

#### Major Development
- Added support for Power-up EventSub interactions
- Added support for Bits, Channel Points, Clips and Hype Train API interactions
    - Get Custom Power-up
    - Create/Delete Custom Reward
    - Get Custom Reward
    - Create Clip
    - Get Clips (by Clip IDs or Broadcaster ID)
    - Get Clips Direct Link
    - Get Hype Train Status
- Expanded version support to cover Unreal 5.4 through to 5.8

#### API Changes
- `GetUsers` Blueprint now has three variants: `GetUsers`, `GetUsersByID`, and `GetUsersByName`
    - `GetUsers` functions as before, requiring both channel IDs **and** usernames to be provided, whilst `GetUsersByID` and `GetUsersByName` provide quicker hookups 
- Made API changes to reflect Twitch 2026-07-31 Changelog:
    - `Send Chat Message` now has the option to pin the sent message
    - `Stream Offline` now includes id
    - `Chat Message` now includes gif fragment 

#### Bug Fixes
- No longer crashes the Editor when `Twitch` input node is not connected in Blueprints
    - `OnFailed` callback is triggered and a message printed in the Output Log

---

### Version 1.1.0

#### Major Development
- None

#### API Changes
- None

#### Bug Fixes
- Fixed build error preventing plugin from compiling correctly

---

### Version 1.0.1

#### Major Development
- None

#### API Changes
- Made API changes to reflect Twitch 2025-06-13 Changelog:
  - Hype Train now v2 implementation

#### Bug Fixes
- None

---

### Version 1.0.0-rc.4

#### Major Development
- None

#### API Changes
- `EChatSender` has been replaced with `EMode`
- `OnChatMessage()`, `OnChatCommand()` and `GetChatters()` now take an `EMode` argument *(see Bug Fixes)*
- Reflects Twitch 2025-05-09 Changelog

#### Bug Fixes
- `OnChatMessage()` and `OnChatCommand()` do not establish EventSub notifications with `AuthenticateChat()`
  - Both functions now take a `Listener` to determine if they should be authenticated as the Broadcaster or the Chatter

---

### Version 1.0.0-rc.3

#### Major Development
- None

#### API Changes
- Reflects Twitch 2025-04-15 Changelog

#### Bug Fixes
- None

---

### Version 1.0.0-rc.2

#### Major Development
- None

#### API Changes
- None

#### Bug Fixes
- `Connect()` only returns successfully if both Chat and Events are authenticated, and fails silently in all other instances.
    - `Connect()` now succeeds in instances where only Chat or Events are authenticated (where applicable)
    - Failure is only invoked if no authentication at all has taken place prior to being called
    - Function no longer silently fails, always triggering an `onSuccess` or `onFailed` callback

---

### Version 1.0.0-rc.1

#### Major Development
- None

#### API Changes
- None

#### Bug Fixes
- Cached tokens are only refreshed during `Authenticate` calls, resulting in invalidated tokens over extended periods of time.
  - All API calls now respond to a *401 Unauthorized* response from the server
  - Tokens are refreshed and the API call re-attempted before failure state is returned
  - Refreshed tokens are stored in the same way as the `Authenticate` calls for use in future API calls

---

### Version 1.0.0

#### Major Development
- Initial release for Unreal Engine 5

#### API Changes
- None

#### Bug Fixes
- None
