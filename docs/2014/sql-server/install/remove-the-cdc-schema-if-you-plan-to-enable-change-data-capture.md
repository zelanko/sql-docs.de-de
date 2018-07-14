---
title: Entfernen Sie die cdc-Schema aus, wenn Sie planen, Change Data Capture aktivieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
caps.latest.revision: 8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f76517b1d97e9304569685ca4df4d3f5a5d57e7f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37222550"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a>Entfernen Sie das CDC-Schema, wenn Sie planen, Change Data Capture zu aktivieren
  Eine Datenbank enthält bereits ein CDC-Schema. Wenn Sie nach dem Upgrade Change Data Capture aktivieren möchten, müssen Sie zuerst dieses CDC-Schema löschen. Wenn Sie eine Datenbank für Change Data Capture aktivieren, erstellt [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ein neues Schema mit dem Namen CDC.  
  
  
