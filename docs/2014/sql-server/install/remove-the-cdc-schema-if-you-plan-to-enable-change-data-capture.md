---
title: Entfernen Sie die cdc-Schema aus, wenn Sie planen, Change Data Capture aktivieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a5d162635a9162871e51fe0664198302804aa487
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855757"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a>Entfernen Sie das CDC-Schema, wenn Sie planen, Change Data Capture zu aktivieren
  Eine Datenbank enthält bereits ein CDC-Schema. Wenn Sie nach dem Upgrade Change Data Capture aktivieren möchten, müssen Sie zuerst dieses CDC-Schema löschen. Wenn Sie eine Datenbank für Change Data Capture aktivieren, erstellt [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ein neues Schema mit dem Namen CDC.  
  
  
