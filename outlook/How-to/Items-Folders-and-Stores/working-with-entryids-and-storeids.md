---
title: Working with EntryIDs and StoreIDs
keywords: vbaol11.chm5274174
f1_keywords:
- vbaol11.chm5274174
ms.prod: outlook
ms.assetid: b27fbb05-1149-c6ae-dfbf-bae8c6c2e93f
ms.date: 06/08/2019
ms.localizationpriority: medium
---


# Working with EntryIDs and StoreIDs

This topic describes using the Entry ID of an item and Store ID of a store to access a specific item in a **[NameSpace](../../../api/Outlook.NameSpace.md)**.

If you are creating a more complex solution using Microsoft Outlook that involves linking or cross-referencing items in folders, one option is to use the MAPI-based identifiers (IDs) of each item. If you know the IDs of an item and the folder it's stored in, you can directly reference the item using the **[NameSpace.GetItemFromID](../../../api/Outlook.NameSpace.GetItemFromID.md)**method.

Each Outlook item has a field called **EntryID**, which is a unique ID field generated by the messaging storage system for use with the MAPI folders that store the item. It's important to note that whenever an item is created in a folder, it is assigned a new **EntryID**. This means that the **EntryID** field changes if an item is moved to a different folder or if an item is exported and then imported (even to the same folder).

Each folder has an ID field called **[Folder.StoreID](../../../api/Outlook.Folder.StoreID.md)**, the value of which is the same for all the folders in a particular message store. Each folder also has a unique Entry ID field.
When using the **GetItemFromID** method to retrieve an item based on its ID, you should specify both the **EntryID** of the item and the **StoreID** of the folder. If you don't specify the **StoreID**, **GetItemFromID** searches the default message store.
The following Microsoft Visual Basic for Applications (VBA) example illustrates the use of the **GetItemFromID** method. The code retrieves the **StoreID** from the default Contacts folder, fills an array ( `MyEntryID`) with the Entry IDs of all of the contacts in the folder, and finally retrieves a specific contact item:



```vb
Sub OutlookEntryID() 
 ' If there are more than 500 contacts, change the following line: 
 Dim MyEntryID(500) As String 
 Dim StoreID As String 
 Dim EntryID As String 
 
 Set olns = Application.GetNamespace("MAPI") 
 Set objFolder = olns.GetDefaultFolder(olFolderContacts) 
 ' Get the StoreID, which is a property of the folder. 
 StoreID = objFolder.StoreID 
 ' Set objAllContacts equal to the collection of all contacts. 
 Set AllContacts = objFolder.Items 
 I = 0 
 ' Loop to get all of the EntryIDs for the contacts. 
 For Each Item In AllContacts 
 I = I + 1 
 MyEntryID(I) = Item.EntryID 
 Next 
 ' Randomly choose the 2nd contact to retrieve. 
 Set Item = olns.GetItemFromID(MyEntryID(2), StoreID) 
 Item.Display 
End Sub
```

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
