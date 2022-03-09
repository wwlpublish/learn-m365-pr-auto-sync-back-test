Now you have connected your encoder. Before you go live with custom produced Live Event, make sure to configure your OBS Studio settings to the following:

Launch OBS, go to **File** -> **Settings** .
Click **Output**, then choose **Advanced** output mode and configure the following settings:
- **Encoder**: If your PC supports hardware encoding pick the one that's not x264 (ex-     Quick Sync H.264, NVENC, etc.). If hardware encoding isn't an option leave it as x264.  
- **Rate Control**: Make sure CBR is selected.  
- **Bitrate**: Enter a value in kbps, 2000 to 4000 is what is normally used. 
- **Keyframe Interval**: 2. 
 
Click **Audio** -> Configure **Track 1** -> **Audio Bitrate**: 128, 160, or 192 for audio encoding.  

Click **Video** and Configure the following settings
- **Base (Canvas) Resolution**: This is your normal desktop resolution (usually 1920 x 1080).
- **Output (Scaled) Resolution**: 1280 x 720 (Encoder Profiles are maxed at 720p in Stream for Live Events).
- **Common FPS Values**: 30 is normally used for frames per second.

Image 

## Extracting content from Teams as a (content source) 
 In our scenario, we are using a Teams meeting as our content source. Remember, this is the Source machine, and it joins the Teams meeting and uses NDI to extract the isolated video feeds and mixed audio feed.  

Image

**The Producer must**: 
- Enable NDI in the Teams client
- Ensure video feeds are active in the Teams client
- Pin select videos as desired (max of 9 video feeds)
- Invoke the Large Gallery (Preview)
- Invoke the Together Mode (Preview) Enable Broadcast over NDI in Teams meeting
- NDI feeds contain mixed audio of all participants, except the user on the Source machine 
 
Image

## Bringing in sources to the Producers Machine (using OBS as an example)
 **Note**: This is the Producer’s machine, and it runs the production software (e.g., OBS, Wirecast, vMix) to produce the desired layouts. From here, you can send the feed to your external audience.
- Install OBS and the OBS NDI Plugin (requires restart) 
- In OBS, create a new Scene, and add a new NDI source

Image

- Select the desired feed and position into the scene

Image

**Note**: both audio and video must be present.

## How to use OBS in a Teams produced live event
*Role - Producer*

Using an external app/encoder to enhance the production of your Teams-produced live event will require  the usage of NDI Tools from NewTek to bring the production stream from the external app/encoder back into the Teams-produced live event or capture card devices amongst other components.  

Some of the advantages to this approach are your ability to leverage the advanced workflows/features found in production software (changing of scenes, adding Lower Thirds, etc.), while also taking advantage of Teams-produced live event features such as Public (anonymous) attendee access and translation. 