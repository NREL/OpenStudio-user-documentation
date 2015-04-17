<h1>The Building Component Library</h1>

The [BCL](https://bcl.nrel.gov) is an online repository of components and measures that can be used in OpenStudio.  Registering on the BCL website provides you with an API key that can be used by the OpenStudio Application to access online components and measures.  BCL users who belong to a group can also upload their own content&mdash;public or private&mdash;to the BCL.  Users can either create a new group or request to join an existing one. The following tutorial provides information on common BCL tasks.

##Groups

###Creating a Group

To create a group, first login to the site and click the *My Dashboard* link at the top right of the BCL site.  Click on the *Create Content* tab, and then the *Group* button.  Fill out the form and click the *Save* button. 

![Create a Group](img/bcl/create_group.png)
*Above: Creating a BCL group.*


A note on group visibility:  if you create a private group, BCL users will not be able to see the group, or request membership.  You will have to manually add all users to the group (see [Adding a Member to a Group](#adding-a-member-to-a-group)).  Additionally, creating a public group does not restrict you to having only public content; a public group can have both public and private content.

Once you submit the form, a BCL admin will be notified and will review your group creation request.  You will receive an email when the group is approved, at which time you can upload content.


###Joining a Group

To join a public group, click the *Groups* button on the BCL homepage.  Select the group you would like to join and click the *Subscribe to Group* or *Request Group Membership* button.  Your membership will be pending until the group admin reviews and approves your request. 

![Request Membership](img/bcl/request_membership.png)
*Above: Requesting group membership.*

###Adding a Member to a Group

If you are a group administrator, you can add members to your group by clicking the *My Dashboard* link at the top right of the page, then clicking on the *My groups* tab. Your group should now be listed on the page. Click on the linked group’s name, which will take you to the group description page. 

![Select Group](img/bcl/select_group.png)
*Above: Selecting your group for viewing.*

Click on the *Group* tab at the top of the page.

![View Group](img/bcl/view_group.png)
*Above: View Group by clicking on the Group tab.*

From this page you can add new members by clicking on the *Add people* link.  

![Add Members](img/bcl/add_members.png)
*Above: Add Members to group.*

New members will need to provide you with their BCL account username. 
 
![Add Member by Username](img/bcl/add_member_username.png)
*Above: Add Member by username.*

###Approving a Membership

If you are the group admin of a public group, you can approved requested memberships to your group by clicking the *My Dashboard* link at the top right of the page and then clicking on the *My groups* tab.  Your group should now be listed on the page.  Click on the linked group's name, which will take you to the group description page.

![Select Group](img/bcl/select_group.png)
*Above: Selecting your group for viewing.*

Click on the "Group" tab at the top of the page.  You can then approve pending memberships by clicking on the *People* link.

![Manage Members](img/bcl/manage_members.png)
*Above: Manage group members by clicking on the People link.*

Check the checkbox next to the pending users to approve, choose *Modify membership status* from the *Operations* dropdown, and press the *Execute* button. 

![Modify Membership Status](img/bcl/modify_membership_status.png)
*Above: Modify membership status.*

Change the membership status to *Active* and click *Next*, then *Confirm*.

![Approve Members](img/bcl/approve_members.png)
*Above: Approve new members.*

You can follow steps similar to these to remove a user from a group.  Check the checkbox next to the user to remove, choose *Remove from Group* from the *Operations* dropdown, and click the *Execute* button.  You can also change a user's group permissions by assigning group roles.  Choose *Modify OG User Role* from the *Operations* dropdown, and click the *Execute button.  Group roles are described in the next section.

###Group Roles

There are 4 roles that users can have relative to the group to which they belong:  group manager, administrator member, editor, and member.


 - **Group Manager**: This role is assigned to the user who created the group.  There is only one group manager per group, and this   user will receive e-mails when other users request membership to the group.

 - **Administrator Member**: Users with the administrator role can assign roles to other group users and approve group membership.  They can also edit the group description and review, publish, and delete group content.

 - **Editor**: Users with the editor role can review and publish group content.

 - **Member**: The member role is the default role assigned to new group members.  These users can create draft content and submit content for review.  An editor or administrator member of the group will then need to review and publish it.


##Uploading and Publishing Content
There are 2 types of content on the BCL:  components and measures.  Components are the building blocks of an energy model, and include roofs, walls, windows, occupancy and equipment schedules, and weather information, to name a few.  Measures describe a change to an energy model for purposes such as comparison to a baseline model or estimation of potential energy savings.

###Uploading a Component
There are two methods of uploading components to the BCL website:  either through an input form or a file upload. **At this time, only the file upload method is compatible with OpenStudio.** Users must be part of a group to upload content, and only group admins can publish content for their group.  

To begin, click on the *My Dashboard* link at the top right of the BCL site.  Click on the *Create content* tab.  You should see a list of buttons.  Press the *Upload Component* button, which will direct you to a multi-tab form.

![Upload Component](img/bcl/upload_component.png)
*Above: Upload a Component.*

The *Data* tab contains a file upload field that will accept either a zip component or a tar.gz component package.  The *Group* tab contains a list of the groups with which you are affiliated.  Select the appropriate group, as well as your desired content visibility for this component (public or private to the group).	Save the form.

![Component Visibility](img/bcl/component_visibility.png)
*Above: Select desired group and component visibility.*

The component package to upload should contain a component.xml file created with the current [component schema](https://bcl.nrel.gov/xsd/component/v/2), available on the [BCL](https://bcl.nrel.gov) website.  The &lt;uid&gt; and &lt;version_id&gt; fields can be left blank as they will be assigned by the BCL.  

Make sure to include the type of your component in the &lt;tag&gt; field. Select from the available [BCL component types](https://bcl.nrel.gov/component-types), and include the full hierarchy.  This is usually 2 or 3 levels separated by a dot.  For example, if you are uploading a weather file component, the &lt;tag&gt; should be: *Location-Dependent Component.Weather File*.  If you do not see a suitable component type for your component in the list, please [contact us](https://www.openstudio.net/contact). 

Attributes can also be applied to components via the component.xml file.  Consult the supported list of [BCL attributes](https://bcl.nrel.gov/list-of-attributes) to view the correct names.  For OpenStudio compatibility, the *OpenStudio Type* attribute should be used.

The package should also contain the associated files referenced inside the component.xml file’s &lt;files&gt; section.  The compressed package should directly contain these files; the upload will fail if the package has an inner directory containing the files.

![Component Package Creation](img/bcl/create_component_package.png)

*Above: Compress the files directly to create the component package; do not compress a directory containing the files.*

###Uploading a Measure
There are two methods of uploading measures to the BCL website:  either through an input form or a file upload. **At this time, only the file upload method is compatible with OpenStudio.** Users must be part of a group to upload content, and only group admins can publish content for their group.  

To begin, click on the *My Dashboard* link at the top right of the BCL site.  Click on the *Create content* tab.  You should see a list of buttons.  Press the *Upload Measure* button, which will direct you to a multi-tab form.

![Upload Measure](img/bcl/upload_measure.png)
*Above: Upload a Measure.*

The *Data* tab contains a file upload field that will accept either a zip measure or a tar.gz measure package.  The *Group* tab contains a list of the groups with which you are affiliated.  Select the appropriate group, as well as your desired content visibility for this measure (public or private to the group).	Save the form.

![Measure Visibility](img/bcl/measure_visibility.png)
*Above: Select desired group and measure visibility.*

The measure package to upload should contain a measure.xml file created with the current [measure schema](https://bcl.nrel.gov/xsd/measure/v/2), available on the [BCL](https://bcl.nrel.gov) website.  The &lt;uid&gt; and &lt;version_id&gt; fields can be left blank as they will be assigned by the BCL.  

Make sure to include the type of your measure in the &lt;tag&gt; field. Select from the available [BCL measure types](https://bcl.nrel.gov/measure-types), and include the full hierarchy.  This is usually 2 or 3 levels separated by a dot.  For example, if you are uploading a space types measure, the &lt;tag&gt; should be: *Whole Building.Space Types*.  If you do not see a suitable measure type for your measure in the list, please [contact us](https://www.openstudio.net/contact).

Attributes can also be applied to measures via the component.xml file.  Consult the supported list of [BCL attributes](https://bcl.nrel.gov/list-of-attributes) to view the correct names.  For OpenStudio compatibility, the *Measure Type* attribute should be used.

The package should also contain the associated files referenced inside the measure.xml file’s &lt;files&gt; section. These files should be contained in directories according to usage type:  the main measure file, usually named *measure.rb* should be compressed directly (same level as measure.xml), resource files should be in a *resources* directory, and test files should be in a *tests* directory. The compressed package should directly contain these files and directories; the upload will fail if the package has an inner directory containing the files.

![Measure Package Creation](img/bcl/create_measure_package.png)

*Above: Compress the files directly to create the measure package; do not compress a directory containing the files.*

###Publishing Content

All members of a group can add content to the BCL, but only users with the *editor* or *administrator member* group roles can review and publish their group's content.  Content can be published by clicking the *My Dashboard* link at the top right of the page, then clicking on the *My content* tab and selecting the *group content* sub-tab. 

![Review Content for Publication](img/bcl/moderate_content.png)
*Above: Review group content.*

Content in either the *Draft* or *Needs Review* states can be published by changing the moderation state to *Published*.  The intended workflow is as follows:

* A content author creates a component or measure.  The content is in the *Draft* state.  
* Once the author is satisfied with the content, he/she sets the state to *Needs Review*.  This indicates to the group editors and administrators that content is ready to be reviewed and published.
* Once reviewed, a group editor or administrator sets the state to *Published.
* The process is repeated for future revisions to the content.





