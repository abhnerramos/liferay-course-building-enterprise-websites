---
uuid: fa59111a-df99-4fec-95d3-690485bf5fe6
---

![Introduction page for day 3](./day-3-exercises-for-building-enterprise-websites-with-liferay/images/01.png)

# Day 3 Exercises for Building Enterprise Websites with Liferay

* [Exercise 19a: Creating an Object Definition](#exercise-19a-creating-an-object-definition)
* [Exercise 19b: Building the Form](#exercise-19b-building-the-form)
* [Exercise 19c: Creating a Dashboard for Contact Us Responses](#exercise-19c-creating-a-dashboard-for-contact-us-responses)
* [Bonus Exercise: Creating a Multi-Step Form](#bonus-exercise-creating-a-multi-step-form)
* [Exercise 20a: Modifying a Theme Client Extension](#exercise-20a-modifying-a-theme-client-extension)
* [Exercise 20b: Deploying a Client Extension for Favicon](#exercise-20b-deploying-a-client-extension-for-favicon)
* [Exercise 20c: Creating a New CSS Client Extension](#exercise-20c-creating-a-new-css-client-extension)
* [Exercise 20d: Setting Up and Deploying the Distributor Application](#exercise-20d-setting-up-and-deploying-the-distributor-application)
* [Exercise 20e: Testing the Distributor Application](#exercise-20e-testing-the-distributor-application)
* [Exercise 20f: Adding Fields to the Distributor Applications Object](#exercise-20f-adding-fields-to-the-distributor-applications-object)
* [Exercise 20g: Adding Picklist Items](#exercise-20g-adding-picklist-items)
* [Exercise 20h: Assigning Object Permissions](#exercise-20h-assigning-object-permissions)
* [Exercise 20i: Enabling the Approval Workflow](#exercise-20i-enabling-the-approval-workflow)
* [Exercise 20j: Automating Account Creation](#exercise-20j-automating-account-creation)
* [Exercise 20k: Setting Up Notifications](#exercise-20k-setting-up-notifications)
* [Exercise 21: Tailoring Experiences by User Group and Role](#exercise-21-tailoring-experiences-by-user-group-and-role)
* [Exercise 22a: Using JMeter to Run Load Tests](#exercise-22a-using-jmeter-to-run-load-tests)
* [Exercise 22b: Auditing Page Performance](#exercise-22b-auditing-page-performance)
* [Exercise 22c: Fixing the Performance Issue](#exercise-22c-fixing-the-performance-issue)
* [Exercise 22d: Reassessing Performance with JMeter](#exercise-22d-reassessing-performance-with-jmeter)

## Exercise 19a: Creating an Object Definition

Clarity wants to create a user-friendly contact form to streamline communication with non-employee users. Liferay Objects provides the tools to build and seamlessly integrate this form with their Contact Us page.

Here you'll create the `Contact Us` object and configure its fields for storing relevant information as the Clarity Admin user.

To do this,

1. Sign in as the Clarity Admin user.

   * Username: `admin@clarityvisionsolutions.com`
   * Password: `learn`

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Objects*.

1. Click *Add* (![Add Button](./../../../../../dxp/latest/en/images/icon-add.png)).

1. Enter these details:

   | Field        | Value      |
   |:-------------|:-----------|
   | Label        | Contact Us |
   | Plural Label | Contact Us |
   | Object Name  | ContactUs  |

1. Click *Save*.

   This creates a draft object definition with some default system fields. You can now configure the definition to determine how its data is stored and which features you want to enable.

1. From the Objects overview page, begin editing the *Contact Us* object definition.

1. In the Details tab, configure these settings:

   | Field                                                   | Value          |
   |:--------------------------------------------------------|:---------------|
   | Scope > Scope                                           | Site           |
   | Scope > Panel Link                                      | Content & Data |
   | Configuration > Show Widget in Page Builder             | False          |
   | Configuration > Enable Entry History in Audit Framework | True           |

1. Click *Save*.

   Now that you’ve configured the object definition, you can add custom fields to determine the type of information you want to gather with the form.

1. Go to the *Fields* tab.

1. Click *Add* (![Add Button](./../../../../../dxp/latest/en/images/icon-add.png)), enter these details, and click *Save*:

   | Field                     | Value      |
   |:--------------------------|:-----------|
   | Label                     | Full Name  |
   | Field Name                | `fullName` |
   | Type                      | Text       |
   | Mandatory                 | Yes        |
   | Accept Unique Values Only | No         |

1. Repeat the previous step to create the remaining fields:

   | Label             | Field Name        | Type      | Mandatory | Unique Values Only |
   |:------------------|:------------------|:----------|:----------|:-------------------|
   | Email Address     | `emailAddress`    | Text      | Yes       | No                 |
   | Phone             | `phone`           | Text      | Yes       | No                 |
   | State or Province | `stateOrProvince` | Text      | No        | No                 |
   | City              | `city`            | Text      | No        | No                 |
   | Comment           | `comment`         | Long Text | No        | N/A                |

1. Return to the *Details* tab and click *Publish*.

   This creates the database tables for storing form submissions.

Next, you'll add the form to Clarity's Contact Us page.

## Exercise 19b: Building the Form

Liferay Objects generates a basic user interface automatically, but you can design and add forms to Clarity’s pages.

Previously, you added and wireframed the Contact Us page. Here you’ll add the form to the page as the Clarity Admin user.

To do this,

1. Go to Clarity’s public enterprise website and begin editing the Contact Us page.

1. Drag and drop a *form container* fragment into the Contact Form container.

1. Click the drop-down menu and select the *Contact Us* object.

1. Select all fields and click *Save*.

1. Select the form container and configure these settings:

   | Tab             | Setting       | Value                |
   |:----------------|:--------------|:---------------------|
   | General > Frame | Width         | 400px                |
   | Styles          | Padding       | Spacer 4 (all sides) |
   | Styles          | Background    | #FFFFFF              |
   | Styles          | Border Radius | 15px                 |

1. Drag and drop the field fragments into this order:

   * Full Name
   * Email Address
   * Phone
   * State or Province
   * City
   * Comment

1. Select each of these field fragments and configure this setting:

   | Tab    | Setting | Value             |
   |:-------|:--------|:------------------|
   | Styles | Padding | Spacer 3 (bottom) |

1. Click *Publish*.

   ![You can fill out the Contact Us form after publishing the page.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/01.png)

1. Test the form by submitting an entry.

1. Go to *Site Menu* (![Site Menu](./../../../../../dxp/latest/en/images/icon-product-menu.png)), expand *Content & Data*, and click *Contact Us*. The entry you created should appear here.

   ![The Contact Us entry appears in the menu.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/02.png)

Great! You've fully set up the Contact Us page and made it available for Clarity's users. Next, you'll create a administrative dashboard for tracking contact requests using frontend data sets.

## Exercise 19c: Creating a Dashboard for Contact Us Responses

As Clarity continues to receive contact requests, its team needs a reliable way to track and respond to submissions. To support this, Clarity wants to define a workflow for the Contact Us object and create dashboard for viewing unanswered requests from site visitors. In this exercise, you’ll implement both of these elements as the Clarity Admin user.

### Creating a Workflow

Here you’ll create a simple workflow that sends a notification to the Distributor Representatives role for new requests.

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)) and click *Process Builder* in the Applications tab.

1. Click *New* to create a new workflow.

1. For name, enter `Contact Us Follow Up`.

1. In the Nodes panel, find the *Task* node and drag it into the workflow editor.

   ![Find the Task node and drag it into the workflow editor.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/03.png)

1. In the side panel, configure these settings for the Task node.

   | Field       | Value                                                               |
   |:------------|:--------------------------------------------------------------------|
   | Label       | Follow Up                                                           |
   | Node Name   | followUp                                                            |
   | Description | Ask Distributor Representative to verify new Contact Us submission. |

1. Hover your mouse over the Start node and drag an arrow to the Task node.

   ![Hover your mouse over the Start node and drag an arrow to the Task node.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/04.png)

1. In the side panel, configure these settings for the Transition Label.

   | Field           | Value                   |
   |:----------------|:------------------------|
   | Label           | Review                  |
   | Transition Name | review_contact_us_entry |
   | Default         | Yes                     |

1. In the same way, drag an arrow from the Task node to the End node.

   ![Drag an arrow from the Follow Up node to the End node.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/05.png)

   This defines the progression of the workflow.

1. In the side panel, configure these settings for the second Transition Label.

   | Field           | Value                    |
   |:----------------|:-------------------------|
   | Label           | Approve                  |
   | Transition Name | approve_contact_us_entry |
   | Default         | Yes                      |

   ![In the side panel, configure these settings for the second transition.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/06.png)

1. Click the *Follow Up* node to begin configuring it.

1. Under Assignments, click *Asset Creator*.

1. For Assignment Type, select *Role*.

1. For Role, select *Distributor Representative*.

   ![For Role, select Distributor Representative.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/07.png)

1. Click *Back* (![Back](./../../../../../dxp/latest/en/images/icon-angle-left.png)) to continue editing the Follow Up node.

1. Under Notifications, click *New*.

1. For Name, enter `Follow Up Task`.

1. For Template, enter this text:

   ```log
   There is a new ${entryType} request for you to follow up with.
   ```

1. For Notification Types, select *User Notification*.

1. For Recipient Type, select *Role*.

1. For Role Name, select *Distributor Representative*.

   ![Edit the Follow Up Task.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/08.png)

1. Click the End node to begin configuring it.

1. Under Actions, click *New*.

1. Set the following attributes for the new action:

   | Field          | Value          |
   |:---------------|:---------------|
   | Name           | Approved Entry |
   | Type           | Updated Status |
   | Status         | Approved       |
   | Execution Type | On Entry       |

1. Click *Publish*.

   ![Publish the workflow.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/09.png)

Clarity now has a workflow that routes entries to users with the Distributor Representatives role. Next, you'll use it with the Contact Us object.

### Attaching the Workflow to the Object

Once you create a workflow, you can configure Liferay applications to use it. Here you'll configure the Contact Us object to use the new workflow.

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)) and go to the *Clarity Public Enterprise Website*.

1. Open the *Site Menu* (![Site Menu](./../../../../../dxp/latest/en/images/icon-product-menu.png)), expand *Configuration*, and select *Workflow*.

1. Click *Edit* for the Contact Us asset type.

1. Select the *Contact Us Follow Up* workflow and click *Save*.

   ![Select the Contact Us Follow Up workflow.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/10.png)

Great! You’ve successfully configured the *Contact Us* object to use the workflow. This ensures that users with the Distributor Representatives role receive notifications for new submissions, so they can review and address reach one. Next, you’ll create a UI for displaying pending tasks.

### Creating the Contact Us Responses Data Set

To help representatives monitor incoming requests, Clarity needs a way to display pending contact submissions in a clear, structured UI. Here you'll enable Liferay Data Sets and use it to implement this UI.

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Instance Settings*.

1. Under the Platform section, click *Feature Flags*.

1. In the Release tab, enable these features:

    * *Root Object Definitions (LPD-34594)*
    * *Data Set Manager (LPS-164563)*

   ![In the Release tab, enable these features.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/11.png)

   Now you can create a data set.

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Data Sets*.

1. Click *Add* to create a new data set and enter these details:

   | Field            | Value                |
   |:-----------------|:---------------------|
   | Name             | Contact Us Responses |
   | REST Application | `/c/contactuses`     |
   | REST Schema      | `ContactUs`          |
   | REST Endpoint    | `/scopes/{scopeKey}` |

   ![Click Add to create a new data set and enter these details.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/12.png)

1. Click *Save*.

1. Click the *Contact Us Responses* data set to begin editing it.

1. Add this parameter to the Parameters input box:

   ```log
   filter=(status/any(x:(x eq 1)))
   ```

   **Note**: This filter checks whether any status value equals `1`, which corresponds to entries in a pending status.

1. Click *Save*.

1. Go to the *Visualization Modes* tab.
Here you can determine what data users can view for different visualizations (i.e., table, list, or cards).

1. Go to the *List* tab.

1. Click *Add* (![Add](./../../../../../dxp/latest/en/images/icon-plus.png)) for the Title row and select *Assign from Data Source*.

   ![Select Assign from Data Source for the Title row.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/13.png)

1. Select the *fullName* field.

   ![Select the fullName field.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/14.png)

1. Click *Save*.

1. Click *Add* (![Add](./../../../../../dxp/latest/en/images/icon-plus.png)) for the Description row and select *Assign from Data Source*.

1. Select the *comment* field.

1. Click *Save*.

   ![Select the comment field for the Description row.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/15.png)

Now when users view the data set as a list, these data points appear. The list should also only include entries with a ‘Pending’ workflow status. Next, you’ll display the data set on a site page.

### Displaying the Data Set on a Page

Clarity wants to display their new data set on a dedicated page. Here you’ll create the Contact Us Responses page and add the data set to it.

1. Go to the *Clarity Public Enterprise Website*.

1. Open the *Site Menu* (![Site Menu](./../../../../../dxp/latest/en/images/icon-product-menu.png)), expand *Site Builder*, and select *Pages*.

1. Click *New* to create a new page.

1. Select the *Primary Master Page* template and name it `Contact Us Responses`.

1. Click *Add*.

1. Drag and drop the *Data Set* fragment into the page’s drop zone.

1. In the General panel, click *Add* (![Add](./../../../../../dxp/latest/en/images/icon-plus.png)) to select a data set.

1. Select the *Contact Us Responses* data set and click *Save*.

   ![Select the Contact Us Responses data set and click Save.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/16.png)

1. Click *Publish*.

   Since no Contact Us entries have been submitted after setting up the workflow, there are currently no pending entries to display.

1. Verify everything works as expected:

   * Use the Contact Us form to submit a few sample entries.
   * Then return to the Contact Us Responses page to see the pending requests appear in the data set.
   * Next, sign in as (or impersonate) Daniel Raymond to confirm that the Distributor Representative received the workflow notifications.
   * Finally, assign the workflow task to Daniel Raymond, approve it, and return to the data set page to confirm the entry has been removed.

   ![Verify everything works as expected.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson19/images/17.png)

Great! The data set is now published on a page, allowing users to view pending Contact Us entries in real time.

Next, you can learn how to create a multi-step form or move to Lesson 20 to learn about Liferay Client extensions and how you can use them to add styling and functionality to your Liferay instance.

## Bonus Exercise: Creating a Multi-Step Form

**Challenge**:

Convert the Contact Us form into a multi-step form for improving user experience.

**Requirements**:

* Use the existing Contact Us object.
* Enable draft mode for the object definition.
* Create two form steps using the Stepper fragment.
* Add a "Next" button for the first step, and "Previous" and "Submit" buttons for the second step.

**Success Criteria**:

The multi-step form collects the information provided by the user on each step.

## Exercise 20a: Modifying a Theme Client Extension

Client Extensions separate customizations from the Liferay core. This helps simplify updates while freeing you to use your desired technologies and deployment models. As seen previously, the global CSS client extension provides a way to extend styling in Liferay DXP. Here you'll update the client extension provided in the training workspace and deploy your changes as Walter Douglas.

To do this,

1. Sign in as Walter Douglas.

   * Email: `walter.douglas@clarityvisionsolutions.com`
   * Password: `learn`

1. In the Clarity Public Enterprise Website, go to the Home page.

   Note that Clarity's "See the Difference" banner uses a beige background (i.e., `#FCFBF8`). Let's make a change to Clarity's theme CSS client extension to update it.

   ![Clarity's "See the Difference" banner uses a beige background.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/02.png)

1. In your training workspace, navigate to the `classroom-exercises/lesson-20/` folder, open the `layout-background-color.scss` file, and copy its contents.

   This file contains styling for overwriting the background color for the `.lfr-layout-structure-item-container` CSS class.

1. Navigate to the `client-extensions/clarity-global-css/` folder, open the `assets/global.css` file, add the copied CSS style to the end of the file, and save your changes.

1. Open a new terminal window, navigate to the `client-extensions/clarity-global-css/` folder, and run this command to build and deploy the client extension:

   ```bash
   blade gw clean deploy
   ```

   Or use Gradle Wrapper:

   ```bash
   ../../gradlew clean deploy
   ```

1. Verify the command executes successfully.

1. If necessary, log out of the Clarity portal. It may also be necessary to clear the cache in the browser if this change is not reflected automatically.

1. Verify the background of the container is now gray:

   ![New gray background](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/03.png)

   **Tip**: When making changes to global CSS values, you may need to clear your browser's cache to see your changes.

1. Now that you have seen how you can modify CSS styles using a global CSS client extension, remove the styling change just made from the `global.css` file.

Next you'll learn how to use client extensions to update the site's favicon.

## Exercise 20b: Deploying a Client Extension for Favicon

In a previous exercise, you set the site favicon manually via the Liferay UI. With client extensions, you can streamline updates to your site by deploying the favicon along with your other frontend client extensions. Here you'll use a client extension to update Clarity's favicon as Walter Douglas.

To do this,

1. Open a new terminal window and go to the `client-extensions/clarity-theme/` folder in your training workspace.

1. Run this command to build and deploy the client extension:

   ```bash
   blade gw clean deploy
   ```

   Or use Gradle Wrapper:

   ```bash
   ../../gradlew clean deploy
   ```

1. Verify the command executes successfully.

1. Open the *Site Menu* (![Site Menu](./../../../../../dxp/latest/en/images/icon-product-menu.png)), expand *Site Builder*, and select *Pages*.

1. Click *Actions* (![Actions](./../../../../../dxp/latest/en/images/icon-actions.png)) in the Application Bar and select *Configuration*.

1. In the Design tab, click *Select Favicon* (![Select Favicon](./../../../../../dxp/latest/en/images/icon-change.png)).

1. In the modal window, go to the *Client Extension* tab and select *Clarity Theme Favicon*.

1. Click *Save*.

1. Go to the Home page and verify the page's favicon was updated.

   ![Go to the Home page and verify the page's favicon was updated.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/04.png)

## Exercise 20c: Creating a New CSS Client Extension

Liferay provides the CSS client extension for adding a single CSS resource to site pages. Here you'll create one of these client extensions using an external cdnjs URL as Walter Douglas user.

To do this,

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the  *Applications* tab, and click *Client Extensions*.

1. Click *Add* (![Add Button](./../../../../../dxp/latest/en/images/icon-add.png)) and select *Add CSS*.

1. For name, enter `Clarity Animation`.

1. For CSS URL, enter `https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css`.

   ![Create a CSS Client Extension.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/05.png)

1. Click *Publish*.

1. Go to the *Home* page in the Clarity Public Enterprise Website.

1. Click *Configure Page* (![Global Menu](./../../../../../dxp/latest/en/images/icon-cog.png)) and select the *Design* tab.

1. Scroll down and click *Add CSS Client Extensions*.

1. Choose *Clarity Animation* and click *Add*.

   ![Add the Clarity Animation CSS Client Extension to the Home page configuration.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/06.png)

1. Scroll down and click *Save*.

   This saves the page as a draft. For the changes to take effect, you must publish the page.

1. Return to the Home page, click *Edit* (![Edit](./../../../../../dxp/latest/en/images/icon-edit.png)), and click *Publish*.

1. Open the *Site Menu* (![Site Menu](./../../../../../dxp/latest/en/images/icon-product-menu.png)), expand *Design*, and click *Fragments*.

1. Under Fragment Sets, click *Clarity Components*.

1. Select the *Clarity Gradient Container* fragment to begin editing it.

1. In your training workspace, navigate to the `classroom-exercises/lesson-20/` folder, open the `clarityanimation.html` file, and copy its content into the fragment's HTML field.

   This adds three CSS animation classes to the fragment from the from the `animate.css` library on [cdnjs](https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css) (i.e., `animate__animated`, `animate__slower`, and `animate__fadeIn`).

   ![Edit the Clarity Gradient Container's fragment HTML field.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/07.png)

1. Click *Publish*.

   Now that you've updated the fragment, you can propagate these changes to existing instances of the fragment in site pages.

1. Click *Actions* (![Actions menu](./../../../../../dxp/latest/en/images/icon-actions.png)) for the Clarity Gradient Container fragment, and select *View Usages*.

1. Check all boxes and click *Propagate*.

   ![Propagate the changes made to Clarity Gradient Container fragment.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/08.png)

   Now, all fragments used throughout the site are updated with the new CSS classes.

1. Go to the Home Page and confirm the animation works.

   The animation now plays every time you refresh or navigate to the Home page.

   ![Clarity Gradient Container](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/09.png)

Next, let's explore how you can use client extensions with Objects to build custom solutions with complex business logic.

## Exercise 20d: Setting Up and Deploying the Distributor Application

   <!-- !!! note Instruction -->

The training workspace includes a batch client extension for quickly setting up two object definitions and their related picklists. The specific process for deploying client extensions depends on your Liferay hosting model (i.e., Self-Hosted, PaaS, or SaaS). However, in all cases, you must add the compiled `.zip` file to the Liferay server's `[Liferay Home]/osgi/client-extensions/` folder. Here you'll deploy the batch client extensions and explore what they include as the Clarity Admin user.

1. In your training workspace, go to the `client-extensions/clarity-distributor-mgmt-batch/` folder.

1. Run this command to build and deploy the client extension:

   ```bash
   blade gw clean deploy
   ```

   Or use Gradle Wrapper:

   ```bash
   ../../gradlew clean deploy
   ```

1. Verify the command executes successfully.

   Two new object definitions and their picklists were added to your Liferay instance. Let's explore them.

1. While logged in as the Clarity Admin user, open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Picklists*.

   Picklists are predefined lists of items that you can use for single select and multi-select fields in object definitions. Here are picklists imported by the batch client extension:

   * D4B8 Annual Purchase Volumes
   * D4B8 Application States
   * D4B8 Assessment Scores
   * D4B8 Business Types
   * D4B8 Decisions
   * D4B8 Distribution Channels
   * D4B8 Distribution Regions
   * D4B8 Order Types
   * D4B8 Product Labels
   * D4B8 Product Types
   * D4B8 Recommendations

   ![Picklists for the object definitions.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/10.png)

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to *Control Panel*, and click *Objects*.

   Here you'll see two new object definitions imported by the batch client extension:

   * D4B8 Distributor Application
   * D4B8 Application Evaluation

   ![Picklists for the object definitions.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/11.png)

   As we're adding more object definitions, let's add a folder for organizing our objects and place the D4B8 objects into it.

1. Click *Add* (![Add Folder Button](./../../../../../dxp/latest/en/images/icon-plus.png)) for Object Folders.

1. For Label, enter `Distributor Management App`.

1. Click *Create Folder*.

   ![Create a new object folder.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/12.png)

1. Click *View in Model Builder*.

   The Objects Model Builder is a graphical interface that displays each object definition as a card and visualizes relationships between them. With it, you can create, manage, and extend data models in the Objects application and quickly configure definitions, fields, and relationships.

1. In the left side panel, click *Actions* (![Actions menu](./../../../../../dxp/latest/en/images/icon-actions.png)) for D4B8 Distributor Application and select *Move to Current Folder*.

   ![Move the D4B8 Distributor Application object definition to the new folder.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/13.png)

1. Repeat this step for D4B8 Application Evaluation.

1. Drag and and drop the cards to reposition them and better see their relationship.

## Exercise 20e: Testing the Distributor Application

   <!-- !!! note Instruction -->

In the following exercises, you'll learn more about these objects and how they're configured. Here you'll create and review a Distributor Application entry as the Clarity Admin user.

To do this,

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)) and go to the *Control Panel* tab. Both D4B8 Application Evaluations and D4B8 Distributor Applications should appear in the Object category.

   ![The Control Panel now shows the Application Evaluations and Distributor Applications menus.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/14.png)

1. Open *D4B8 Distributor Applications*.

1. Click *Add* (![Add Button](./../../../../../dxp/latest/en/images/icon-add.png)) to create an entry.

1. Fill out the required fields and click *Save*.

   **Note**: You must enter a business name. We'll use this value with client extensions in a later exercise.

1. Return to the Distributor Applications overview page and verify your entry appears in the table.

   ![The created application entry is displayed in the Distributor Application menu.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/15.png)

   Now you can create an evaluation for this entry.

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *D4B8 Application Evaluations*.

1. Click *Add* (![Add Button](./../../../../../dxp/latest/en/images/icon-add.png)) to create an entry.

1. In the Application to Evaluations field, select the application you created. It is identified by the Business Name field.

   <!--TASK: Update the definition to use the Business Name instead of the ID.-->

1. Fill out the evaluation form and click *Save*.

1. Return to the Application Evaluations overview page and verify the entry appears in the table.

   ![The evaluation entry appears in the Application Evaluations menu.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/16.png)

   This evaluation is automatically related to the selected application. You can confirm these entries are related by returning to *Distributor Applications* overview page, selecting the application, and going to the *Evaluation Notes* tab.

   ![The Evaluation Notes tab displays evaluations related to the application.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/17.png)

## Exercise 20f: Adding Fields to the Distributor Applications Object

   <!-- !!! note Instruction -->

The Distributor Applications object already contains several custom fields, but Clarity needs one for applicants to list other brands they offer. Here you’ll add a field to the Distributor Applications Object as the Clarity Admin user.

To do this,

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Objects*.

1. Click the *Distributor Management App* folder.

1. Click *View in Model Builder*.

1. Look for the *D4B8 Distributor Application* object, click *Add Field or Relationship*, then select *Add Field*.

1. Enter these values and click *Save*:

   | Field                    | Value                         |
   |:-------------------------|:------------------------------|
   | Label                    | Business Other Brands Offered |
   | Field Name               | `businessOtherBrandsOffered`  |
   | Type                     | Long Text                     |
   | Enable Entry Translation | False                         |
   | Mandatory                | False                         |

   ![Clicking Add opens a panel to create a new custom field.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/18.png)

   Each saved field is added immediately to the object and automatically appears in its default layout when creating entries. However, the Distributor Application object has a custom layout that must be modified to include the new field.

   Now you'll add the field to the object's layout.

1. Click *Actions* (![Actions Button](./../../../../../dxp/latest/en/images/icon-actions.png)) for D4B8 Distributor Application and select *Edit in Page View*.

1. When prompted, select *Open Page View*.

1. Go to the *Layouts* tab and click *Application Layout*.

1. Go to the *Layout* tab.

1. Find the Business Details block and click *Add Field*.

   ![The Business Details can be found under the Application tab.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/19.png)

1. Select *Business Other Brands Offered* as an option, choose the single column box for the field size, and click *Save*.

   ![Clicking Add Field opens a panel to include a field to the block.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/20.png)

1. Click *Save* at the bottom of the panel.

Now the new field appears in the layout when creating entries.

## Exercise 20g: Adding Picklist Items

   <!-- !!! note Instruction -->

Clarity uses picklists to create predefined options for the applicants to choose from. Currently, the Product Types picklist is empty and does not include any options. Here you'll add items to the picklist as the Clarity Admin user.

To do this,

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Picklists*.

1. Select *D4B8 Product Types*.

1. Click *Add* (![Add Button](./../../../../../dxp/latest/en/images/icon-add.png)) and create these items:

   | Name       | Key        |
   |:-----------|:-----------|
   | Eyeglasses | eyeglasses |
   | Sunglasses | sunglasses |
   | Lenses     | lenses     |
   | Contacts   | contacts   |
   | Other      | other      |

1. Click each item and replace their External Reference Code with these values:

   | Name       | External Reference Code |
   |:-----------|:------------------------|
   | Eyeglasses | PRODUCT_TYPE_EYEGLASSES |
   | Sunglasses | PRODUCT_TYPE_SUNGLASSES |
   | Lenses     | PRODUCT_TYPE_LENSES     |
   | Contacts   | PRODUCT_TYPE_CONTACTS   |
   | Other      | PRODUCT_TYPE_OTHER      |

   ![All picklists should appear after adding them.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/21.png)

1. Click *Save*.

Once saved, the Distributor Application's `Products of Interest` custom field is updated with the selected picklist values. This allows applicants to choose their desired products from the updated list.

<!--TASK: Improve; this is the first time we've mentioned Products of Interest.-->

## Exercise 20h: Assigning Object Permissions

   <!-- !!! note Instruction -->

Clarity wants to allow all authenticated users to submit distributor applications. Here you'll grant the default *User* role permission to access Distributor Applications and add entries as the Clarity Admin user.

To do this,

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Roles*.

1. Select the *User* role and go to the *Define Permissions* tab.

1. In the left menu, go to *Control Panel* &rarr; *Object* &rarr; *D4B8 Distributor Applications*.

1. Add these permissions:

   | Permission                                                             |
   |:-----------------------------------------------------------------------|
   | Application Permissions: Add to Page                                   |
   | Application Permissions: View                                          |
   | Resource Permissions > D4B8 Distributor Applications: Add Object Entry |
   | Resource Permissions > D4B8 Distributor Application: Delete            |
   | Resource Permissions > D4B8 Distributor Application: Update            |

   <!--TASK: Confirm whether the delete and update permissions are necessary. I suspect they are not necessary, since entry creators are assigned the entry 'owner' role, which allows them to update for delete the entry.-->

   ![The User role should be able to create, read, update, and delete applications.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/22.png)

1. Click *Save*.

1. Verify the User role has the desired permissions.

   ![All permissions are assigned to the User role after configuration.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/23.png)

   Clarity also wants to allow members of their business development team to review all applications and fill out evaluations. To achieve this, let's grant the Business Development Manager role the necessary permissions.

1. Return to the *Roles* overview page and select *D4B8 Business Development Manager*.

1. Go to the *Define Permissions* tab.

1. In the left menu, go to *Control Panel* &rarr; *Object* &rarr; *D4B8 Distributor Applications*.

1. Add these permissions, and click *Save*:

   * D4B8 Distributor Applications

     | Permission                                                  |
     |-------------------------------------------------------------|
     | Application Permissions: Access in Control Panel            |
     | Application Permissions: View                               |
     | Resource Permissions > D4B8 Distributor Application: Update |
     | Resource Permissions > D4B8 Distributor Application: View   |

   * D4B8 Application Evaluations

     | Permission                                                            |
     |-----------------------------------------------------------------------|
     | Application Permissions: Access in Control Panel                      |
     | Application Permissions: View                                         |
     | Resource Permissions > D4B8 Application Evaluations: Add Object Entry |
     | Resource Permissions > D4B8 Application Evaluation: Add Discussion    |
     | Resource Permissions > D4B8 Application Evaluation: Delete            |
     | Resource Permissions > D4B8 Application Evaluation: Delete Discussion |
     | Resource Permissions > D4B8 Application Evaluation: Update            |
     | Resource Permissions > D4B8 Application Evaluation: Update Discussion |
     | Resource Permissions > D4B8 Application Evaluation: View              |

   ![All permissions are assigned to the Business Development Manager Role after configuration.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/24.png)

1. For test purposes, go to the *Assignees* tab and assign this role to Harper Roberts.

Great! Now Clarity can make sure the business development team's manager can view submitted applications, create evaluations, and approve or deny applications. Next, let's finish setting up Clarity's workflow.

## Exercise 20i: Enabling the Approval Workflow

   <!-- !!! note Instruction -->

Clarity has already implemented a workflow process for reviewing and approving changes made to applications, but this workflow depends on a [microservice client extension](../../../../../dxp/latest/en/development/integrating-microservices.md) to function properly. Currently, all updates to the *Application State* field are approved automatically. However, the workflow is supposed to require a final manager review before allowing users to set the *Application State* field to `Approved` or `Denied`.

<!--TASK: Improve; this is the first time we mention the state field.-->

Here you'll deploy the microservice client extension and finish configuring the workflow definition in the Liferay UI as the Clarity Admin user.

To do this,

1. Open your terminal and go to the `[repository-root]/client-extensions/clarity-distributor-mgmt-action/` folder.

1. Build and deploy the client extension project into your Liferay instance. Make sure the deployment was successful.

   ```bash
   blade gw clean deploy
   ```

   Or use Gradle Wrapper:

   ```bash
   ../../gradlew clean deploy
   ```

1. Run this command from the `clarity-distributor-mgmt-action/` folder to start the Spring Boot application:

   ```bash
   blade gw bootRun
   ```

   Or use Gradle Wrapper:

   ```bash
   ../../gradlew bootRun
   ```

1. When the application starts, go to http://localhost:58081/ready. If the application is ready for use, the page says “READY”.

1. In your Liferay instance, open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Applications* tab, and click *Process Builder*.

   ![The Distribution Manager Approval workflow displays in the workflows menu.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/25.png)

   The Distribution Manager Approval workflow is already fully configured. All you have to do is enable it for the Distributor Application object.

1. Go to the *Configuration* tab.

1. Click *Edit* for D4B8 Distributor Application, select *D4B8 Distribution Manager Approval*, and click *Save*.

   ![The assigned workflow will be used by the object.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/26.png)

This enables the workflow. Now you can test it by editing an object entry and setting its state field to *Under Review*. This update should be approved automatically by the workflow action. Next, update the state field to `Approved`. The entry's status should be `Pending`. You can then impersonate Harper Roberts and check for a workflow notification. You can then assign the task to Roberts and approve it. Once finished, the entry's status should be `Approved`.

## Exercise 20j: Automating Account Creation

To complete the onboarding flow, Clarity wants to automate account creation for approved applications. The client extension you deployed in the previous exercise includes an object action client extension for this. When triggered, this action creates an account using the application's business name, associates the applicant with the account, and assigns the applicant the Account Administrator role. Since the client extension is already deployed and the microservice is running, all you have to do is create an object action to finish setting it up as the Clarity Admin user.

To do this,

1. Begin editing the *D4B8 Distributor Application* object.

1. Go to the *Actions* tab and click *Add* (![Add Button](./../../../../../dxp/latest/en/images/icon-add.png)).

1. Enter these values in the Basic Info tab:

   | Field        | Value                                                              |
   |:-------------|:-------------------------------------------------------------------|
   | Action Label | Set Up Account                                                     |
   | Action Name  | setUpAccount                                                       |
   | Description  | Standalone, create a business account for an approved application. |
   | Active       | True                                                               |

1. Go to the *Action Builder* tab and set these values:

   | Field         | Value                                                                                    |
   |:--------------|:-----------------------------------------------------------------------------------------|
   | Trigger       | Standalone                                                                               |
   | Action        | `object-action-executor[function#clarity-distributor-mgmt-action-object-action-account]` |
   | Error Message | Failed to create the business account.                                                   |

1. Click *Save*.

   ![Create a new action called Set Up Account for D4B8 Distributor Application object.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/27.png)

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Roles*.

1. Add the Set Up Account action permission to the D4B8 Business Development Manager role.

1. In the left menu, go to *Control Panel* &rarr; *Object* &rarr; *D4B8 Distributor Applications*.

   | Permission                                                               |
   |--------------------------------------------------------------------------|
   | Resource Permissions > D4B8 Distributor Application: action.setUpAccount |

When saved, Liferay adds the Set Up Account action as an option in each object entry's *Actions* menu (![Actions Button](./../../../../../dxp/latest/en/images/icon-actions.png)), so you can trigger it manually. Now you can try it out!

![Liferay adds the Set Up Account action as an option in each object entry's Actions menu.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/28.png)

After triggering the action, open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Accounts*. If successful, the new account should appear.

## Exercise 20k: Setting Up Notifications

   <!-- !!! note Instruction -->

Currently, Clarity's distributor management app only includes notifications for notifying applicants of changes in their application's status. But they do not have notifications for alerting their business development team of new submissions. Relying on team members to manually check for new submissions does not scale and leaves room for human error, resulting in missed opportunities or poor user experience.

Here you'll add a notification template and set up an object action for triggering it as the Clarity Admin user.

To do this,

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Templates* under Notifications.

   The provided solution includes these templates:

   * Application Approved
   * Application Denied
   * Application Received

   ![The provided solution includes three notification templates.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/29.png)

1. Click *Add* and select *User Notification*.

   Here you can begin designing the template.

   **Tip**: You can access object field references to populate notifications dynamically with data for the entry or user who triggers the notification action. To view available variables, scroll down to Definition of Terms and select *D4B8 Distributor Application* object in the dropdown menu.

1. Enter these values for Basic Info:

   | Field       | Value                                                                                                 |
   |:------------|:------------------------------------------------------------------------------------------------------|
   | Name        | `D4B8 Application Submitted, Admin, User`                                                             |
   | Description | `Sends user notifications to an administrative role whenever a distributor application is submitted.` |

   <!--TASK: ![]() -->

1. Enter these values for Settings:

   | Field      | Value                             |
   |:-----------|:----------------------------------|
   | Recipients | Role                              |
   | Role       | D4B8 Business Development Manager |

   <!--TASK: ![]() -->

1. Enter this value for Content:

   | Field   | Value                                                                                                                                                                      |
   |:--------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Subject | `APP-[%D4B8DISTRIBUTORAPPLICATION_ID%]: [%D4B8DISTRIBUTORAPPLICATION_APPLICANTNAME%] submitted a distributor application for [%D4B8DISTRIBUTORAPPLICATION_BUSINESSNAME%].` |

1. Click *Save*.

   Now you can add a notification action to the Distributor Applications object that uses this template.

1. Open the *Global Menu* (![Global Menu](./../../../../../dxp/latest/en/images/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Objects*.

1. Select *D4B8 Distributor Application* and go to the *Actions* tab.

   The provided solution includes three notification actions:

   * Application Received
   * Application Approved
   * Application Denied

   ![The provided solution includes three notification actions.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/30.png)

1. Click *Add* to create a new object action.

1. Enter these values in the Basic Info tab:

   | Field        | Value                                                     |
   |--------------|-----------------------------------------------------------|
   | Action Label | Application Submitted                                     |
   | Action Name  | applicationSubmitted                                      |
   | Description  | On After Add, send notifications to administrative users. |
   | Active       | True                                                      |

   ![Clicking Add opens a sidebar to create a new object action.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/31.png)

1. Go to the *Action Builder* tab and set these values:

   | Field                 | Value                                   |
   |-----------------------|-----------------------------------------|
   | Trigger               | On After Add                            |
   | Condition             | N/A                                     |
   | Action                | Notification                            |
   | Notification Template | D4B8 Application Submitted, Admin, User |

   ![The Action Builder tab is used to set the trigger, condition, and action to be done.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/32.png)

1. Click *Save*.

Now whenever users submit an application, employees with the Business Development Manager role are automatically notified. To test the notification, create another application entry and impersonate Harper Roberts. You should see a platform notification.

![A notification is sent to the business manager when an application is submitted.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson20/images/33.png)

## Exercise 21: Tailoring Experiences by User Group and Role

Segmentation involves grouping website visitors and users into categories based on shared characteristics or behaviors. Segmenting your audience allows you to tailor the website experience, delivering more relevant content and ultimately boosting engagement.

Here, you'll create a segment specifically for Distributor users as the Clarity Admin user.

To do this,

1. Sign in as the Clarity Admin user.

   * Email: `admin@clarityvisionsolutions.com`
   * Password: `learn`

1. Add a new user with the following attributes.

   | Field         | Value                                                                     |
   |:--------------|:--------------------------------------------------------------------------|
   | Image         | `[repository-folder]/classroom-exercises/lesson-21/terrence-wheatley.png` |
   | Screen Name   | `terrencewheatley`                                                        |
   | Email Address | `terrence.wheatley@oculusdistributors.com`                                |
   | Job Title     | `Distributor Representative`                                              |
   | First Name    | `Terrence`                                                                |
   | Last Name     | `Wheatley`                                                                |
   | Password      | `learn`                                                                   |

   <!--TASK: mail's reference needs to be changed -->

1. Add Terrence Wheatley to the Distributors user group.

1. Open the *Site Menu* (![Site Menu](./../../../../../dxp/latest/en/images/icon-product-menu.png)), expand *People*, and select *Segments*.

1. Click *New* to create a segment.

1. For title, enter `Distributors`.

1. From the Properties menu, use the User section and drag the *Regular Role* into the main part of the screen.

1. Leave the condition as `equals` and use the Select button to choose the Distributor Representative role.

1. From the Properties menu, use the User section and drag the *User Group* into the main part of the screen.

1. Leave the condition as `equals` and use the Select button to choose the Distributors user group.

1. Change the conjunction to `Or`.

   We cover both scenarios here: users in the user group and those with the directly assigned Distributor Representative role.

   ![Set the regular role to Distributor and the user group to Distributors.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson21/images/01.png)

1. Click *View Members* to validate Terrence Wheatley and Daniel Raymond meet the segment condition.

1. Click *Save*.

1. Go to the home page and click *Edit* (![Edit](./../../../../../dxp/latest/en/images/icon-edit.png)).

1. Click the *Experience* drop-down at the top of the page and choose *New Experience*.

1. For the Experience Name enter `Distributor`.

1. For the Audience, choose *Distributors*.

1. Click *Save*.

1. Click *Prioritize Experience* (![Prioritize Experience](./../../../../../dxp/latest/en/images/icon-angle-up.png)) on the Distributor row to position the segment above the Default item.

   **Note:** The experience order determines their priority. Internally, Liferay checks the segments a user belongs to and uses the match with the highest priority.

   Once the Distributor role is re-positioned, the label on the record should now read Active.

1. Modify the title text in the Banner to say `Welcome Back! Elevate Your Inventory with Premium Eyewear`.

1. Hide the Distributor Promo container, since distributors don't need to apply.

1. Click *Publish*.

1. You can test the different experiences through the Simulation menu (![Simulation menu](./../../../../../dxp/latest/en/images/icon-simulation.png)) in the Application Bar.

1. Choose to Preview By Segments. Then, use the Segment dropdown menu to toggle between `Anyone` and `Distributor` and view the corresponding changes in the main window.

1. Impersonate Terrence Wheatley or Daniel Raymond to see the changes.

## Exercise 22a: Using JMeter to Run Load Tests

JMeter is an open-source, performance and load testing tool. Here you'll use it to check the performance of Clarity's site.

**Note**: Depending upon test scenarios, a laptop with more resources (RAM and CPU) would be preferred.

To do this,

1. Execute JMeter on your machine.

1. From the *File* menu, click *Open*.

1. In your training workspace, navigate to the `classroom-exercises/lesson-22/` folder and select the `Clarity.jmx` file.

   ![Open the Clarity.jmx file in JMeter.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson22/images/01.png)

1. From the *Run* menu, click *Start*.

   The test will take a few minutes to run depending on your setup. The clock in the upper right corner displays the time while the test is running. Once the time stops, the test is complete.

1. In the left menu, click *Thread Group* to expand the section and click *Summary Report*.

1. Review the report to find any performance outliers.

   ![Notice that the Summary Report highlights an issue with the blog page.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson22/images/02.png)

1. In the left menu, click *Response Time Graph*.

1. Under the Settings tab, click *Display Graph*.

   This graph can also be used to identify performance outliers.

## Exercise 22b: Auditing Page Performance

Here you'll use the Page Audit Tool to investigate the problem page as the Clarity Admin user.

1. In your Liferay instance, go to problem page to investigate the performance issue.

1. Click *Page Audit* (![Page Audit](./../../../../../dxp/latest/en/images/icon-page-audit-tool.png)) in the Application Bar.

   The Page Audit side panel displays a list of all page fragments sorted by the load time from longest to shortest.

   ![The Page Audit side panel displays a list of all page fragments by load time.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson22/images/03.png)

1. In the Performance tab, identify the fragments with the longest load time.

Next, you'll examine this fragment and fix it.

## Exercise 22c: Fixing the Performance Issue

Here you'll edit the slow fragment to fix the performance issue as the Clarity Admin user.

To do this,

1. Open the *Site Menu* (![Site Menu](./../../../../../dxp/latest/en/images/icon-product-menu.png)), expand *Design*, and click *Fragments*.

1. Begin editing the problem fragment you identified in the previous exercise.

1. In the HTML window, delete the `[#assign x = sleeper.sleep(3) /]` line.

   ![Delete the line causing the performance problem.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson22/images/04.png)

1. Click *Publish*.

1. Propagate the changes made to the fragment to all instances where the fragment is used in Clarity's site.

With the problem fragment fixed, you can retest the Clarity site.

## Exercise 22d: Reassessing Performance with JMeter

Run another performance test with JMeter to verify the fix.

1. Back in JMeter, from the *Run* menu, click *Clear All*.

1. From the *Run* menu, click *Start* to run the load test again.

1. When finished, review the Summary Report and the Response Time Graph again. Notice that the page that previously had a performance issue no longer has a problem.

   ![Notice that the page that previously had a performance issue no longer has a problem.](./day-3-exercises-for-building-enterprise-websites-with-liferay/lesson22/images/02.png)

1. In your Liferay instance, check the problem page again with the Page Audit Tool.

   Notice that the slow loading fragment issue has been resolved.

Congratulations! You've completed all exercises for day three of Building Enterprise Websites with Liferay. Next, you'll test what you've learned.