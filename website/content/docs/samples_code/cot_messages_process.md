---
title: "CoT Message Process"
description: ""
icon: "article"
date: "2024-03-22T10:06:32+01:00"
lastmod: "2024-03-22T10:06:32+01:00"
draft: false
weight: 530
---

This page describes how to log information from a WinTAK plugin.

### Contents

- [CoT](#cot-object)
- [Code Examples](#code-examples)
    - [Processing Incoming CoT Messages](#processing-incoming-cot-messages)

___

<br>

## CoT object

## Code examples

### Processing incoming CoT messages

```cs
To hook the event handler run - 

cotMessageReceiver.MessageReceived += cotMessageReceiver_MessageReceived;
Then add this method -

private void cotMessageReceiver_MessageReceived(object sender, CoTMessageArgument e)
{
     System.Diagnostics.Debug.WriteLine("Received CoT Message - " + e.CotEvent.ToString());
     e.Handled = true; //Set to true stops the standard processing of this message.
}         

```
