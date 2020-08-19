---
description: catalog.master_properties (SSISDB-Datenbank)
title: catalog.master_properties (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09e13f54b3e7ee92ed72b055246ea1235845448f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422054"
---
# <a name="catalogmaster_properties-ssisdb-database"></a>catalog.master_properties (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Zeigt die Eigenschaften des ausgewählten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Masters an.

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Der Name der Scale Out Master-Eigenschaft.|  
|property_value|**nvarchar(max)**|Der Wert der Scale Out Master-Eigenschaft.|

## <a name="remarks"></a>Hinweise
In dieser Sicht wird für jede Scale Out Master-Eigenschaft eine Zeile angezeigt. In dieser Sicht werden folgende Eigenschaften angezeigt:

|Eigenschaftenname|BESCHREIBUNG|  
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
