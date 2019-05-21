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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 97cde3fcfb5effa7c61fde6673a830f67d9fc634
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65714563"
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Zeigt die Eigenschaften des ausgewählten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Masters an.

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Der Name der Scale Out Master-Eigenschaft.|  
|property_value|**nvarchar(max)**|Der Wert der Scale Out Master-Eigenschaft.|

## <a name="remarks"></a>Remarks
In dieser Sicht wird für jede Scale Out Master-Eigenschaft eine Zeile angezeigt. In dieser Sicht werden folgende Eigenschaften angezeigt:

|Eigenschaftsname|Beschreibung|  
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
