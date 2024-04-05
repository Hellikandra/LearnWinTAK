---
title: "MapItem Object"
description: ""
icon: "article"
date: "2024-03-22T10:06:32+01:00"
lastmod: "2024-03-22T10:06:32+01:00"
draft: false
weight: 520
---

This page describes how to log information from a WinTAK plugin.

### Contents

- [MapItem object](#mapitem-object)
- [Code Example](#code-example)
    - [Select](#select)
    - [Pan and Zoom](#pan-and-zoom)
    - [Loop all available](#loop-all-available)
    - [CoT associated](#cot-associated)
___

<br>

## MapItem object

## Code example

### Select 

The example code here present the way to select a MapItem.

```cs
MapMarker mm= mapGroupManager.GetMapObject(item.UID).GetMapMarker();
mm.IsSelected = true;
```

### Pan and Zoom

The example code present the possibility to pan and zoom on a specific MapItem.

```cs
MapItem mapitem = mapGroupManager.GetMapObject(item.UID);
var message = new FocusMapMessage(new TAKEngine.Core.GeoPoint(mapitem.GetObjectPosition())){
    Behavior = WinTak.Common.Events.MapFocusBehavior.PanAndZoom,
};
messageHub.Publish(message);
```

### Loop all available

This snippet code show how to retreive all available MapItem object.

```cs
foreach (var m in mapGroupManager.MapItems)
{
    MapMarker mm = m.GetMapMarker();
    System.Diagnostics.Debug.WriteLine("Found map object - " + m.Name);
}
```

### CoT avaialble

The snippet code show how to parse the CoT information from a specific MapItem object. In this example, we consider that the CoT XML contains a node :
```xml
<companyX device="helloworld" />
```
    
```cs
MapItem mapitem = mapGroupManager.GetMapObject(item.UID);
string device = m.GetCotEvent().ToXml().GetElementsByTagName("companyX")[0].Attributes["device"].Value;
```