# Documentation

**Sitecore JSS React - Trackable Links**

## Category:
Best enhancement to JSS to change a JSS component rendering behavior based on user's session data

## Submission:
**Trackable Links Module** 
> Empower marketers to trigger any goal or event from Sitecore link fields in JSS.

Inspired by the SBOS team's previous work, this Trackable Links module enables content authors and marketers in Sitecore 9.1 JSS to associate Sitecore Goals and Events to general link fields. Both Content Editor and Experience editor link dialogs are supported. A &lt;TrackableLink /&gt; ReactJS component is offered as an extension of the default Sitecore &lt;Link /&gt; component. This component will seemlessly apply the intended goals and events in the JSS platform  to the user's interaction when the link is clicked. This compliments Sitecore's default behaviour of tracking on page view and tightens focus on user click choices. Use cases include A/B testing multiple CTAs to the same page, tracking of external links, and many more! All of these data points empower marketers to personalize messaging to the visitor. 

## Pre-requisites:

Does your module rely on other Sitecore modules or frameworks?

- Sitecore 9.1 XP0
- Enable anonymous Indexing on xConnect (See [here](https://doc.sitecore.com/developers/91/sitecore-experience-platform/en/enable-indexing-of-anonymous-contacts.html))
- Install **[Sitecore JavaScript Services Server for Sitecore 9.1 XP]** on Sitecore Instance [Link]
(https://dev.sitecore.net/Downloads/Sitecore_JavaScript_Services/110/Sitecore_JavaScript_Services_1100.aspx)

## Installation:

- Install **Sitecore 9.1 (XP0 Single)**, Select **$Prefix = "sc910"** (domain to be **http://sc910.sc**)
- Install **[Sitecore JavaScript Services Server for Sitecore 9.1 XP]** on Sitecore Instance [Link]
(https://dev.sitecore.net/Downloads/Sitecore_JavaScript_Services/110/Sitecore_JavaScript_Services_1100.aspx)
- Update xconnect config to enable anonymous indexing (Switch **IndexAnonymousContactData** to true)
  - [xconnect root path]\App_Data\jobs\continuous\IndexWorker\App_data\config\sitecore\SearchIndexer\sc.Xdb.Collection.IndexerSettings.xml
  - [xconnect root path]\App_Data\Config\Sitecore\SearchIndexer\sc.Xdb.Collection.IndexerSettings.xml
- Restart all xConnect services
- Add JSS host and binding
  - In your local hosts file add **(127.0.0.1 sc910.sc.jssdemo)**
  - Add **sc910.sc.jssdemo** to your Sitecore iis bindings 
- Install Demo Package from Sc.Package folder [Sitecore React Trackable Links Module and Demo-1.0.zip](https://github.com/Sitecore-Hackathon/2019-Sitecorps/raw/master/sc.package/Sitecore%20React%20Trackable%20Links%20Module%20and%20Demo-1.0.zip "Sitecore React Trackable Links Module and Demo-1.0.zip")  and then Select **Overwrite all**
- Publish Site
- Rebuild Index (need master and core indexed for module to fully work)
- Deploy marketing definitions (Goals and Events only) from Control Panel 

![Deploy Marketing Definition](images/Deploy-marketing-definitions.png?raw=true "Deploy Marketing Definition")


## Configuration:

Everything should be included in the provided package and steps above

## Usage:

The provided package will include demo items that we will explain how it works and how it can be used in other areas

-  New **TrackableLink** React component added by module package extends the original Link Field component to include tracking.
- Content editor and Experience editor dialogs for Sitecore link fields have been extended to allow marketers to specify a goal or event to trigger for link.
- To use this component, you can reference it from any React component like this, Note that the usage of TrackableLink is the same as the original Link, so it still support all the Link features and properties:
![Trackable Link Usage](images/TrackableLinkUsage.png?raw=true "Trackable Link Usage")
- Thats it! thats all you need to start tracking links from within general link field, Next will show you how would you select goal/event and how to personalize content based on visitor clicks
- In our demo, We created a template with two links, Each one will trigger differnt Goal, Go to /sitecore/content/demo/home/TrackingLinks and open experience editor, You will see this component on the page:
![Trackable Link Rendering Example](images/TrackableLinkRendering.png?raw=true "Trackable Link Rendering Example")
- Choose one of links fields, and click on "Edit Link" button and you will see the following screen where you set goal or event for this link:
![Insert Link Dialog](images/InsertLinkDialog.png?raw=true "Insert Link Dialog")
- Do the same for the other Link field
- If you clear your session by going to http://sc910.sc.jssdemo/sitecore/api/jss/track/flush, this will flush the current user session and submit it to xConnect, You can go to Analytics Reports to view the registered goals/events
![Goals Report](images/LinksReports.png?raw=true "Goals Report")

- To personalize content based on user clicks, you can simply use sitecore default conditional rules, For this demo we applying personalization based on triggered goal for the user session, We created another content component on the same page to show that once you click the link you can immediately see personalization applied:

![Personalized Content](images/PersonalizedContent.png?raw=true "Personalized Content")

## Want to See this in action in the demo site?
- Go to http://sc910.sc.jssdemo/TrackingLinks
- Click on any of the link of the page (You like Red or Blue color?)
- You will imediately start seeing personalized content based on what you have clicked!

## --- NOTE ---
With Sitecore JSS React Tracking API, there seem to be a bug when used in **Firefox browser** where the async call does not execute correctly when we call onClick event for an anchor (We even added alert to wait for the exeuction to finish but it still didnt work), we are opening an issue in Sitecore JSS repo for this.

## Video:

https://www.youtube.com/watch?v=tGimhgij-00

[![Watch our video on Youtube](https://img.youtube.com/vi/tGimhgij-00/0.jpg)](https://www.youtube.com/watch?v=tGimhgij-00)
