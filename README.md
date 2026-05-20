<?xml version="1.0" encoding="UTF-8"?>
<OfficeApp xmlns="http://schemas.microsoft.com/office/appforoffice/1.1"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:bt="http://schemas.microsoft.com/office/officeappbasictypes/1.0"
  xmlns:mailappor="http://schemas.microsoft.com/office/mailappversionoverrides/1.0"
  xsi:type="MailApp">

  <Id>a1b2c3d4-e5f6-7890-abcd-ef1234567890</Id>
  <Version>1.0.0.0</Version>
  <ProviderName>Trisect Commercial</ProviderName>
  <DefaultLocale>en-US</DefaultLocale>
  <DisplayName DefaultValue="Trisect Inbox Manager" />
  <Description DefaultValue="Auto-file emails by project, snooze, and keep your inbox clean." />

  <Hosts>
    <Host Name="Mailbox" />
  </Hosts>

  <Requirements>
    <Sets>
      <Set Name="Mailbox" MinVersion="1.8" />
    </Sets>
  </Requirements>

  <FormSettings>
    <Form xsi:type="ItemRead">
      <DesktopSettings>
        <SourceLocation DefaultValue="https://YOUR-HOSTING-URL/taskpane.html" />
        <RequestedHeight>250</RequestedHeight>
      </DesktopSettings>
    </Form>
  </FormSettings>

  <Permissions>ReadWriteMailbox</Permissions>
  <Rule xsi:type="RuleCollection" Mode="Or">
    <Rule xsi:type="ItemIs" ItemType="Message" FormType="Read" />
  </Rule>

  <VersionOverrides xmlns="http://schemas.microsoft.com/office/mailappversionoverrides" xsi:type="VersionOverridesV1_0">
    <Requirements>
      <bt:Sets>
        <bt:Set Name="Mailbox" MinVersion="1.8" />
      </bt:Sets>
    </Requirements>

    <Hosts>
      <Host xsi:type="MailHost">
        <DesktopFormFactor>
          <FunctionFile resid="Commands.Url" />

          <!-- Reading pane ribbon buttons -->
          <ExtensionPoint xsi:type="MessageReadCommandSurface">
            <OfficeTab id="TabDefault">
              <Group id="trisect.group1">
                <Label resid="GroupLabel" />

                <!-- File Now button -->
                <Control xsi:type="Button" id="trisect.FileNow">
                  <Label resid="FileNowLabel" />
                  <Supertip>
                    <Title resid="FileNowLabel" />
                    <Description resid="FileNowDesc" />
                  </Supertip>
                  <Icon>
                    <bt:Image size="16" resid="Icon.16x16" />
                    <bt:Image size="32" resid="Icon.32x32" />
                    <bt:Image size="80" resid="Icon.80x80" />
                  </Icon>
                  <Action xsi:type="ExecuteFunction">
                    <FunctionName>fileEmailNow</FunctionName>
                  </Action>
                </Control>

                <!-- Snooze button -->
                <Control xsi:type="Button" id="trisect.Snooze">
                  <Label resid="SnoozeLabel" />
                  <Supertip>
                    <Title resid="SnoozeLabel" />
                    <Description resid="SnoozeDesc" />
                  </Supertip>
                  <Icon>
                    <bt:Image size="16" resid="Icon.16x16" />
                    <bt:Image size="32" resid="Icon.32x32" />
                    <bt:Image size="80" resid="Icon.80x80" />
                  </Icon>
                  <Action xsi:type="ExecuteFunction">
                    <FunctionName>snoozeEmail</FunctionName>
                  </Action>
                </Control>

                <!-- Open Task Pane button -->
                <Control xsi:type="Button" id="trisect.OpenPane">
                  <Label resid="OpenPaneLabel" />
                  <Supertip>
                    <Title resid="OpenPaneLabel" />
                    <Description resid="OpenPaneDesc" />
                  </Supertip>
                  <Icon>
                    <bt:Image size="16" resid="Icon.16x16" />
                    <bt:Image size="32" resid="Icon.32x32" />
                    <bt:Image size="80" resid="Icon.80x80" />
                  </Icon>
                  <Action xsi:type="ShowTaskpane">
                    <SourceLocation resid="Taskpane.Url" />
                  </Action>
                </Control>

              </Group>
            </OfficeTab>
          </ExtensionPoint>
        </DesktopFormFactor>
      </Host>
    </Hosts>

    <Resources>
      <bt:Images>
        <bt:Image id="Icon.16x16" DefaultValue="https://YOUR-HOSTING-URL/assets/icon-16.png" />
        <bt:Image id="Icon.32x32" DefaultValue="https://YOUR-HOSTING-URL/assets/icon-32.png" />
        <bt:Image id="Icon.80x80" DefaultValue="https://YOUR-HOSTING-URL/assets/icon-80.png" />
      </bt:Images>
      <bt:Urls>
        <bt:Url id="Commands.Url" DefaultValue="https://YOUR-HOSTING-URL/commands.html" />
        <bt:Url id="Taskpane.Url" DefaultValue="https://YOUR-HOSTING-URL/taskpane.html" />
      </bt:Urls>
      <bt:ShortStrings>
        <bt:String id="GroupLabel" DefaultValue="Trisect" />
        <bt:String id="FileNowLabel" DefaultValue="File Email" />
        <bt:String id="SnoozeLabel" DefaultValue="Snooze" />
        <bt:String id="OpenPaneLabel" DefaultValue="Inbox Manager" />
      </bt:ShortStrings>
      <bt:LongStrings>
        <bt:String id="FileNowDesc" DefaultValue="Move this email to its matching project folder." />
        <bt:String id="SnoozeDesc" DefaultValue="Snooze this email to reappear later." />
        <bt:String id="OpenPaneDesc" DefaultValue="Open the Trisect Inbox Manager panel." />
      </bt:LongStrings>
    </Resources>
  </VersionOverrides>
</OfficeApp>
