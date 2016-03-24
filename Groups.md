
# Groups

 **Last modified:** February 08, 2016

 _**Applies to:** Skype for Business 2015_

## What is a group?

A group object is the visual metaphor of a person list view. A [Group](http://technet.microsoft.com/library/6cf7a1b7-d732-422b-96e6-ff8ac18cedc8%28Office.14%29.aspx) object can be a collection of individual people or it can be a distribution group that is composed of people and other distribution groups. A group can come from any of these sources. Groups are used to create a person list view organized by people groupings.


### Groups

The [Application](http://technet.microsoft.com/library/e0969542-53e2-473a-b02f-2554b01451f1%28Office.14%29.aspx).[PersonsAndGroupsManager](http://technet.microsoft.com/library/ce912c52-5bed-47b1-b4e0-ce4328297c87%28Office.14%29.aspx) object provides access to all[Group](http://technet.microsoft.com/library/6cf7a1b7-d732-422b-96e6-ff8ac18cedc8%28Office.14%29.aspx) objects. The **PersonsAndGroupsManager.all** property returns a single "all" **group**. The "all"[Group](http://technet.microsoft.com/library/6cf7a1b7-d732-422b-96e6-ff8ac18cedc8%28Office.14%29.aspx) **.groups** property returns a collection of **group** objects.

The collection returned by  **.groups** contains a **group** of each type including relationship groups, user-created or a server-created[Group](http://technet.microsoft.com/library/6cf7a1b7-d732-422b-96e6-ff8ac18cedc8%28Office.14%29.aspx) objects. The server created groups include distribution groups and "frequent persons". User created groups are known as "custom groups" and owned by the signed in user. Custom group membership is maintained by using the Skype for Business client.


### Relationships

A collection of relationship [Group](http://technet.microsoft.com/library/6cf7a1b7-d732-422b-96e6-ff8ac18cedc8%28Office.14%29.aspx) objects is a grouping of persons by work relationship. **RelationshipLevel** include Colleagues, Workgroup, or Blocked.


### Nested Distribution groups

A nested distribution group is a distribution group whose parent is a distribution group. Figure 1 shows a collection of distribution groups returned by a search query. The selected distribution group is opened to show its contents. The distribution group includes two people and another distribution group: "Engineering Desktop Dev All" 


**Figure 1. Nested distribution groups in Skype for Business**

![SkypeWebSDK_ConvObjects](images/7bb0af54-be7a-4c3b-a41c-516b8e7bcd04.png) 

The scenario shown by figure 1 is represented in the Skype Web SDK object model by figure 2. The red connector in the diagram represents the nested relationship between parent and child person groups.

The groups collection on the  **application.PersonsAndGroupsManager.all.groups** object represents person groups that a user has added to her person list. This collection can include custom groups and distribution groups. A collection of **groups** returned in a search query contains only distribution groups. Read[PersonsAndGroupsManager](http://technet.microsoft.com/library/ce912c52-5bed-47b1-b4e0-ce4328297c87%28Office.14%29.aspx) for information about searching for distribution groups.


**Figure 2. Group recursion to represent nested distribution groups**

![SkypeWebSDK_GroupRecursionObjectmodel](images/98268a50-4d6f-4969-be93-2c7a81fe57a8.png) 

**Nested distribution group persons**: Instead of getting all persons and groups at all nesting levels with one operation, an application must get persons from the **group.persons** collection on distribution group objects at each nesting level. To get deeper nesting levels, an application gets groups from the **group.groups** collection of the current nesting level.


## What can you do with a group?

Build a dynamic view of a user's person list with content from the Groups collection. A group in Skype Web SDK is a read-only object. You can get the name and URI of a person group along with the persons and groups that it contains. You can register a listener callback method to react to changes in the membership of a person group. The listener lets you keep the person list view current. Although a user cannot change the membership of a person group using a Skype Web SDK app, she can change the group by using the native client.

 **Supported clients**

Internet Explorer 10 and later, Safari 8 and later, FireFox 40 and later, and Chrome 43 and later.


## See also


#### Concepts


[Search for persons and distribution groups]( /SearchForPersonsAndGroups.md)<br/>
[Manage persons and groups]( /ManagePersonsAndGroups.md)