No Neutral Core

This mode stops Neutral Zones from generating. (prior to that sectors discovery)
It is advised to add this mod prior to players entering the core.

The distance modification can be changed by changing the number 150 to any value you would like to measure from the center:

    if self.templates[i].path == 'sectors/neutralzone' and distanceFromCenter < 150 then


INSTRUCTIONS:

You have two choices:
A). Download and drag and drop the data folder into the Avorion directory.
    This option is NOT advised for servers with multiple mods, as replacing the sectorspecifics.lua file will revert other mods changes to this file
      Clients are not required to have this file when playing on a server.

B). Edit your current SectorSpecifics.lua file and change/add these lines of code:
    Use the Downloaded file or view the github source to identify the precise location inside sectorspecifics.lua you need to change.

    --self.generationTemplate = self.templates[i]
    --Commented out by Dirtyredz | David McClain

    --Begin Added by - Dirtyredz | David McClain
    local distanceFromCenter = length(vec2(x,y))
    if self.templates[i].path == 'sectors/neutralzone' and distanceFromCenter < 150 then
        print('Sector is set to a neutralZone and inside the core, Reverting to a Colony sector....')
        self.generationTemplate = self.templates[1]
    else
        self.generationTemplate = self.templates[i]
    end
    --End Added by - Dirtyredz | David McClain

DOWNLOAD:
  https://github.com/dirtyredz/NoNeutralCore/releases/download/1.0.0/NoNeutralCore.v1.0.0.zip

GITHUB:
  https://github.com/dirtyredz/NoNeutralCore

UNINSTALL:

Simply remove the "Added by" lines of code and uncomment this line of code:

    --self.generationTemplate = self.templates[i]
