---
description: RDS-Ereignisse
title: RDS-Ereignisse | Microsoft-Dokumentation
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], RDS
- RDS events [ADO]
ms.assetid: e03739e0-8169-46d6-9956-556b644a7645
author: rothja
ms.author: jroth
ms.openlocfilehash: be38e4897e942e30af61937c326cd2efa16a1fd8
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724371"
---
# <a name="rds-events"></a>RDS-Ereignisse
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
|Ereignis|BESCHREIBUNG|  
|-|-|  
|[OnError (RDS)](./onerror-event-rds.md)|Wird aufgerufen, wenn während eines Vorgangs ein Fehler auftritt.|  
|[onleserystatechange (RDS)](./onreadystatechange-event-rds.md)|Wird immer dann aufgerufen, wenn sich der Wert der Eigenschaft " **leserystate** " ändert.|