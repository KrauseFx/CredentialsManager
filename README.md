CredentialsManager
===================

`CredentialsManager` is used by most components in the [fastlane.tools](https://fastlane.tools) toolchain.

All code related to your username and password can be found here: [password_manager.rb](https://github.com/KrauseFx/CredentialsManager/blob/master/lib/credentials_manager/password_manager.rb)

## Storing in the keychain

By default, your Apple credentials are stored in the OS X Keychain.

Your password is only stored locally on your computer.

## Change Password

You can easily delete the stored password by opening the "Keychain Access" app, switching to *All Items*, and searching for "*deliver*". Select the item you want to change and delete it. Next time running one of the tools, you'll be asked for the new password.

## Using environment variables

```
DELIVER_USER
DELIVER_PASSWORD
```

If you don't want to have your password stored in the Keychain use `FASTLANE_DONT_STORE_PASSWORD`.

## Implementing a custom solution

All ```fastlane``` tools are Ruby-based, and you can take a look at the source code to easily implement your own authentication solution.

```ruby
require 'credentials_manager'

data = CredentialsManager::AccountManager.new(user: user, password: password)
puts data.user
puts data.password
```

# License

This project is licensed under the terms of the MIT license. See the LICENSE file.

> This project and all fastlane tools are in no way affiliated with Apple Inc. This project is open source under the MIT license, which means you have full access to the source code and can modify it to fit your own needs. All fastlane tools run on your own computer or server, so your credentials or other sensitive information will never leave your own computer. You are responsible for how you use fastlane tools.
