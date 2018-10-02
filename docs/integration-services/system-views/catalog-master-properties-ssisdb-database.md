---
title: catalog.master_properties (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85b3388be32ac33382ad34f12ec135e84313cb33
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687442"
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Zeigt die Eigenschaften des ausgewählten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Masters an.

|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Der Name der Scale Out Master-Eigenschaft.|  
|property_value|**nvarchar(max)**|Der Wert der Scale Out Master-Eigenschaft.|

## <a name="remarks"></a>Remarks
In dieser Sicht wird für jede Scale Out Master-Eigenschaft eine Zeile angezeigt. In dieser Sicht werden folgende Eigenschaften angezeigt:

|Eigenschaftsname|und Beschreibung|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|Die SQL Server-Instanz, die die Protokolldatenbank enthält.|
|**LAST_ONLINE_TIME**|Zeitpunkt, zu dem der Scale Out Master zuletzt online war.|
|**MACHINE_IP**|Die IP-Adresse des Computers.|
|**MACHINE_NAME**|Der Name des Computers.|
|**MASTER_ADDRESS**|Der Endpunkt des Scale Out Masters.|
|**MASTER_SERVICE_PORT**|Der Port im Endpunkt des Scale Out Masters.|
|**SSLCERT_THUMBPRINT**|Der Fingerabdruck des Scale Out Master-Zertifikats.|

## <a name="permissions"></a>Berechtigungen
Alle Mitglieder der öffentlichen Datenbankrolle besitzen die Leseberechtigung für diese Sicht. 
