# buzzyello README

This is the README for your extension "buzzyello". After writing up a brief description, we recommend including the following sections.

## Features

```plantuml
@startuml "Connect to Airvantag"

crat_v4_3.CRAT_v4_3 -> crat_functions.CRAT : check_imsi_and_mcc_mnc_after_get_last_data_point
activate crat_functions.CRAT
crat_functions.CRAT -> at_manager.SerialATManager : connect_to_airvantage
activate at_manager.SerialATManager
at_manager.SerialATManager -> at_manager.SerialATManager : check_data_connection_to_airvantage
note right
# check AirVantage server
        connection state
# Connect to Airvantage
        (AT+WDSS=1,1)
# On none +WDSI: notifications raise failure
end note
at_manager.SerialATManager -> at_manager.SerialATManager : read_serial_port with timeout=180
deactivate at_manager.SerialATManager

crat_functions.CRAT -> at_manager.SerialATManager : wait_for_airvantage_connection
deactivate crat_functions.CRAT

activate at_manager.SerialATManager
at_manager.SerialATManager -> at_manager.SerialATManager : check_airvantage_connection_response
note right
check thanks to +WDSI: notifications
    that the connection has been successful
end note
@enduml
deactivate at_manager.SerialATManager
```

Describe specific features of your extension including screenshots of your extension in action. Image paths are relative to this README file.

For example if there is an image subfolder under your extension project workspace:

\!\[feature X\]\(images/feature-x.png\)

> Tip: Many popular extensions utilize animations. This is an excellent way to show off your extension! We recommend short, focused animations that are easy to follow.

## Requirements

If you have any requirements or dependencies, add a section describing those and how to install and configure them.

## Extension Settings

Include if your extension adds any VS Code settings through the `contributes.configuration` extension point.

For example:

This extension contributes the following settings:

* `myExtension.enable`: enable/disable this extension
* `myExtension.thing`: set to `blah` to do something

## Known Issues

Calling out known issues can help limit users opening duplicate issues against your extension.

## Release Notes

Users appreciate release notes as you update your extension.

### 1.0.0

Initial release of ...

### 1.0.1

Fixed issue #.

### 1.1.0

Added features X, Y, and Z.

-----------------------------------------------------------------------------------------------------------

## Working with Markdown

**Note:** You can author your README using Visual Studio Code.  Here are some useful editor keyboard shortcuts:

* Split the editor (`Cmd+\` on macOS or `Ctrl+\` on Windows and Linux)
* Toggle preview (`Shift+CMD+V` on macOS or `Shift+Ctrl+V` on Windows and Linux)
* Press `Ctrl+Space` (Windows, Linux) or `Cmd+Space` (macOS) to see a list of Markdown snippets

### For more information

* [Visual Studio Code's Markdown Support](http://code.visualstudio.com/docs/languages/markdown)
* [Markdown Syntax Reference](https://help.github.com/articles/markdown-basics/)

**Enjoy!**
