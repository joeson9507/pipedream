# Getting Started

You can install the Pipedream Discord app in the [Accounts](https://pipedream.com/accounts) section of your account, or directly in a workflow.

### Webhooks

If you happen to stumble on the error: `UNKNOWN_EXCEPTION: admin operation already in progress` when creating an **Instant** trigger, you can follow the steps below to use the Salesforce Flow Builder to be able to use webhooks with Pipedream. This is a known error in Salesforce.

1. Create a New Workflow on [Pipedream](https://pipedream.com) and [add a HTTP trigger](https://pipedream.com/docs/workflows/steps/triggers/#http).
2. Login and go to your [Salesforce Setup Menu Page](https://help.salesforce.com/s/articleView?id=sf.basics_nav_setup.htm&type=5).
3. On the left hand Quick Find Bar, search for **Outbound Messages** in **Process Automation -> Workflow Actions**.
4. Click on the **New Outbound Message** button in the middle of the page.
5. Select the **Object Type** and click **Next**.
6. Fill in the **Name, Unique Name, and Available Fields to Send** fields in the form. On the **Endpoint URL** field, paste the **URL endpoint** generated by the HTTP trigger created earlier and then click **Save**.
7. Back to the left hand Quick Find Bar, search for **Flows** in **Process Automation**.
8. Click on **New Flow** button on the upper right hand corner and then select on **Record-Trigged Flow** and click on Create.
9. Select the same **Object Type** as before and select the appropriate flow trigger.
10. Optionally set **Entry Conditions**, keep **Actions and Related Records** selected, and click on **Done**.
11. Click on the plus sign below the newly created trigger and click on **Action**.
12. Search for **Outbound Message** and on the search bar select the trigger that was created previously.
13. Insert a **Label** and an **API Name** and then click on **Done**.
14. Save the flow by clicking on the **Save** button, insert a **Flow Label** and a **Flow API Name** and then click on **Activate** next to the Save button.
15. Back to the Pipedream Workflow, create a new step with the **Salesforce Convert SOAP Object** action.
16. In the **XML Soap Object** field, select the path from the trigger or type in `{{steps.trigger.event.body}}`.
17. That's it! You can now deploy the workflow and you will receive instant updates from Salesforce.
