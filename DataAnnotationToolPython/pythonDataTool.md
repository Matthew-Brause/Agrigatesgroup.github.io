# Python Data Viewer
This first build of the data viewer is for internal bug testing from the Agrigates Team. This version of the data viewer does not have any installer prepared so a little preparation will need to be done before operation is possible. Please do the following:
## Folder Setup
The data tool requires several folders/files to operate, please setup as follows
```
data tool/
    appData/
        actions.json
    parsed data/
        exampleData.csv
        {any other csv files}
    video/
        YYYYMMDD/
            HH/
                MM.mp4
    dataToolAlpha1.0.exe {dataToolAlpha1.0.x86_64}
```

## Operation
When the application is run, it will open a file explorer dialog, navigate to the CSV file that you would like to view and press `Open`. The data tool should now open and look like the following:
![dataToolLandingPage](./assets/background.png)
If this is seen, you are ready to test the data viewer!

## Controls
### Play/Pause - play or pause the video/data
![play icon](./assets/pauseBtn.png)

### Forward/Backward Button - moves video and data feed forward/backward by one entry
![forward button](https://media.discordapp.net/attachments/989267870527651872/1164457036608720907/forwardBtn.png?ex=65434820&is=6530d320&hm=d2ab59f4e6d96ab6eec411df9a1340fb9043d76c5e451fea2be38b8be5723a76&=)
![backward button](https://media.discordapp.net/attachments/989267870527651872/1164457036331888711/backBtn.png?ex=65434820&is=6530d320&hm=44629aa241494752b94dad4359d0953564a0809a6b846878018b248f4a12d288&=)

### Skip Forward/Backward Button - moves the video and data feed forward/backward by `Skip Jump Interval`
![skip forward button](https://media.discordapp.net/attachments/989267870527651872/1164457037585973288/skipForwardBtn.png?ex=65434820&is=6530d320&hm=b7dd4c76b04b72d3efa8193055ecbdf5f66cfd2f0d377cd4bac24d03acde3c5d&=)
![skip backward button](https://media.discordapp.net/attachments/989267870527651872/1164457037342724166/skipBackBtn.png?ex=65434820&is=6530d320&hm=cfe849d4cd3587dd2958345a41e4fac08ede105aecd45cf2a2c968f6d2decd77&=)

### Set Action In - sets the beginning timestamp of the current observed action to the current index (rightmost portion of the data graph)
![action in button](https://media.discordapp.net/attachments/989267870527651872/1164457037791506522/zoneInBtn.png?ex=65434820&is=6530d320&hm=33e637170be8b281a67b332155725945e70d55689e1e36829f49741738a0cf9a&=)

### Set Action Out - sets the end timestamp of the current observed action to the current index (rightmost portion of the data graph)
![action out button](https://media.discordapp.net/attachments/989267870527651872/1164457038047367239/zoneOutBtn.png?ex=65434820&is=6530d320&hm=9caeafcd66c4dc85236e7b56da8920ce8de27d41fc28c503351b893d5219e971&=)

### Check Boxes - allows for manual control of intervals/window settings/navigation/action exporting/etc
![check box](https://media.discordapp.net/attachments/989267870527651872/1164458695434965043/checkBtn.png?ex=654349ab&is=6530d4ab&hm=d2cdac93dbf8d7c2850e51fe4f2c84699ba4bf0e2d981ef7402c423f073e1ce0&=)

## Operation
To use the data tool all you need to do is:
- Use the play/pause/skip buttons to navigate to the start of an action that you want to label
- Press the Set Action In Button
- Use the controls to navigate to the end of the observed action
- Press the Set Action Out Button
- Choose the desired action from the actions drop down menu
- Press the check box to the right of the drop down
- Rinse and repeat!

## Changing plots
If you want to change plots, you can use the `Plot` dropdown at the top of the tool and select from either the preset options on the top `Acceleration, Magnetometer, Gyro, ...` to change the plots to the (W),X,Y,Z components of that plot type. Or you can use the bottom options to set custom plots. If you want to see only X components you can choose the X components of individual plots in their respective sub-menus.

## Narrowing Scrollbar
if you would like to narrow down the scrollbar to have finer controls. Please use the menu Scrollbar -> Set Edges... option, this will give you a secondary GUI for entering the start and stop indexes that you would like the scrollbar to be between.

## Common Errors
### After opening a csv file, the tool crashes without showing any data
Please make sure that the `appData` folder exists and that the `actions.json` file is in that folder.
#### actions.json
```json
{
    "actions": [
        "Test Action 1",
        "Test Action 2"
    ],
    "labeledData": [
        {
            "actionTimeIn": "2023-09-12T16:23:40.511Z",
            "actionTimeOut": "2023-09-12T16:23:51.233Z",
            "actionType": "eating",
            "file": "Big_Blue.csv"
        },
        {
            "actionTimeIn": "2023-09-12T17:01:51.511Z",
            "actionTimeOut": "2023-09-12T17:02:15.233Z",
            "actionType": "sleeping",
            "file": "Big_Orange.csv"
        }
    ]
}
```

### How do I set more actions/change the current actions?
Please open the `appData/actions.json` file and add any actions you want as the following:
```json
{
    "actions": [
        "Action 1",
        "Action 2",
        ...
        "Action n"
    ],
...
```

### I can only see a `Media could not be found` error
Please ensure that the video folder/sub-folder structure is formatted as specified as:
```
data tool/
    appData/
        actions.json
    parsed data/
        exampleData.csv
        {any other csv files}
    video/
        YYYYMMDD/
            HH/
                MM.mp4
    dataToolAlpha1.0.exe {dataToolAlpha1.0.x86_64}
```