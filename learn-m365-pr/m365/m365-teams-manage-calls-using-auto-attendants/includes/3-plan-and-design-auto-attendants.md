Organizations often want to automate the direction of incoming calls to the right team or call queue. They may also want to complete an interaction by gathering information from a caller's keypad. You can use auto attendants for these tasks.

Suppose you've decided, in your digital camera company, to gather information about callers' technical issues by asking them to select from menus using their keypad. You'll use this information to route the call to the right support team, who each specializes in a different camera series. You've planned a set of menus and you want to know if you can implement them in Microsoft Teams.

Here you'll plan, design, and create auto attendants that are tailored to specific business needs.

## Assess the business need

The first stage of auto attendant planning is to assess the business requirements. Complete the following steps:

### Who are the people in the business?

Create a list of users within the business and identify their roles.

### Why are the customers calling?

The most frequent customer needs should get addressed first. Imagine that Julie  is acting as the Operator for the support desk until the auto attendant system is implemented. She should be in the best position to tell you what customer needs generate calls.
Ask her to keep a record of the calls the business gets and which users she transfers the calls to in response to customer inquiries. This record could look something like this:

|Caller issue  |Number of calls  |Action  |
|---------|---------|---------|
|Scheduling/rescheduling/cancelling appointments    |45         |  No transfer, receptionist handles the call       |
|Billing questions    | 22         | Transfer to Jakob or Laura in billing        |
|Inquiry about hours and business location   | 20         | No transfer, receptionist handles the call        |
|Want to speak to the office manager  | 12         | Transfer to the office manager       |
| | |

### What special considerations does each job function in the office have?

Have some discussions with people in each of the job functions in the office about what they need from the Auto Attendant.

### What language requirements do the customers have?

The countries where you do business are likely to influence the languages spoken by your customers.

Suppose we discover that there were only two callers in the whole week who spoke what seemed like English as a second language. They spoke good enough English to make their inquiries and they didn't seem to speak the same native language. If you confirm this with the business partners, you might decide that menus can be implemented in English only, but bear in mind that you may lose customers who don't speak English well.

#### What are the business hours, non-business hours and holidays?

You may want distinct initial greetings for business hours, after-hours, weekends, and holidays.

### For each of the job functions in the office, what issues do they handle for customers?

You may be surprised by what issues the various office workers usually handle. For example, it's possible that Julie, the receptionist, can answer many questions you assume need the input of the billing department.

## Design and mockup

To complete the initial design, you'll need a flexible and easy way to work out hierarchies and structures of users and auto attendants. You can do this on any blank wall or whiteboard, using several colors of pen and some sticky notes or index cards. Below are some steps that are worth considering as you design:

1. Write on a note or card the name and phone number of each person with a voicemail account in the business. You may need several notes for the operator. It might help to distinguish users and auto attendants with different colored notes.
1. Mark one note as the main auto attendant, which will include a business hours initial greeting, an after-hours greeting, and a main menu. You may also want an auto attendant to represent the hours and location recording and additional auto attendants to cover the needs of your callers. If possible, use a different color of note to represent auto attendants.
1. Place the main auto attendant note on your board space. If any of the top options go directly to a single employee, put their note to the right of the note representing the attendant.
1. It's unlikely all the options will fit on the main auto attendant menu, so think about which additional attendants might be needed and how they might nest under the main attendant.
1. If you have an option that leads to a call queue, create a note using a third color and place it below and to the right of the attendant that connects to the call queue.

:::image type="content" border="false" source="../media/3-aa-lawyeroffice-callqueues.png" alt-text="Example auto attendant design":::

## Write the scripts

Your auto-attendant script can make or break the impression left on your customers or callers. Plan them carefully and consider having them professionally recorded. The goal is to connect the caller to a live person as efficiently as possible.

## Implement auto attendants

Implementation of the design in the earlier diagram is presented in the steps that follow. This implementation uses text-to-speech for the scripts. Phone System has a built-in text to speech engine so you have the option of listening to your final text to determine whether it conveys the impression you want. If not, it's up to you whether to record your own prompts using recording software or have a professional voice-over artist use your scripts to record audio files.

Create the following auto attendant and set its general information.

:::image type="content" source="../media/3-auto-attendant-step1.png" alt-text="Create Auto Attendant":::

In the above image, you'll see that the various fields have been numbered 1 through 5. Here is an example of the values you might use:

1. Give the name of the auto attendant: **Contoso – Top AA**.
1. From the **operator** list, select a person in your organization, for example: **Julia Wolfe**.
1. Select the **Time zone** for this auto attendant, for example: **(UTC-04:00) Eastern Daylight Time (US & Canada)**
1. Choose the **Language** you want to use for prompts, greetings, etc., for example: **English (United Kingdom)**.
1. Finally, decide if you want the caller to be able to verbally respond to menu prompts.

Selecting **Enable voice inputs** will enable voice commands in menus. It will also enable callers to say "Operator" and get transferred directly to the operator.

Next, you can set up **Call flow** for the main menu.

:::image type="content" source="../media/3-call-flow.png" alt-text="Call Flow":::

   In the image above, we've marked the key fields that you'll need to complete with the numbers 1 through 5, and suggested values or options that you can use.

   1. In the **First play a greeting message**, type the message that you want to be read to the caller. For example: Welcome to contoso.
   1. In the **Route the call** section, type the message that the caller will hear prior to hearing the options.
   1. From the **Set menu options**, add in each of the options that you want, for example:

      1. The name that will be read is **Scheduling**, which will **Send to**, **Julie Wolfe**.
      1. The name that will be read is **Billing**, which will **Send to** the voice app and trigger the **Billing** auto attendant.
      1. The name that will be read is **Hours**, which will **Send to** the voice app and trigger the **Hours and Locations** auto attendant.

   1. For the Directory Search, select **Dial by name**

The company greeting is usually only set on the main menu. A nested auto attendant usually flows straight through to the Custom Prompt.

From here, you can usually leave the defaults set for call flows outside business hours, custom call flows during holidays, and dial scope.

### Nested auto attendants

Nested auto attendants don't usually have phone numbers associated or a company greeting, and they only get accessed as directed in the main auto attendant.

Set up the general information for the nested auto attendants using different names but the same time zone, language, speech recognition, and operator settings.

### Test and edit auto attendants

After you've saved your auto attendant, it's listed on the auto attendants page of the admin center. The page also shows some of the options that you set up.
The best way to test the implementation is to call the number configured for an auto attendant and choose options to navigate to each of the new auto attendants. You can also quickly place a test call to your auto attendant with the Test button in the Action pane. If you want to edit an auto attendant, select it, and then in the Action pane click Edit.

## Learn more

- [Planning and implementing auto attendants](/MicrosoftTeams/tutorial-org-aa)
