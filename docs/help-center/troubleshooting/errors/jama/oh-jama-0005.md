## Description

When you encounter error OH-Jama-0005, then following error message will appear:  
**Error message:** OH-Jama-0005: Error occurred while creating entity in target because Set does not exist for Entity Type: `<Entity type>`. You must create a set for this entity.

A set is a structural container item with configurable access rights, used to group items of the same type. It can also contain folders, text items, child text items and child items of the same type.

## Cause

Probable cause for this issue is:  
When Jama system is target, if we do not have a Default set created under the given entity type.

## Solution

In Jama, create a set for given entity type under the Project.
