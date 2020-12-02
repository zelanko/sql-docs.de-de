---
description: catalog.catalog_properties (SSISDB-Datenbank)
title: catalog.catalog_properties (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/11/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: e604a382-95c8-4764-b268-742eb5c6d4cf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7aa744bd7dd3d0330dc3e996b2af90d500be9d55
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96129504"
---
# <a name="catalogcatalog_properties-ssisdb-database"></a>catalog.catalog_properties (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt die Eigenschaften des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalogs an.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Der Name der Katalogeigenschaft.|  
|property_value|**nvarchar(256)**|Der Wert der Katalogeigenschaft.|  
  
## <a name="remarks"></a>Bemerkungen  
 In dieser Sicht wird eine Zeile für jede Katalogeigenschaft angezeigt.
  
|Eigenschaftenname|BESCHREIBUNG|  
|-------------------|-----------------|  
|**DEFAULT_EXECUTION_MODE**|Der serverweite Standardausführungsmodus für Pakete, `Server` (0) oder `Scale Out` (1). |
|**ENCRYPTION_ALGORITHM**|Der Typ des Verschlüsselungsalgorithmus, mit dem sensible Daten verschlüsselt werden. Die unterstützten Werte lauten: `DES`, `TRIPLE_DES`, `TRIPLE_DES_3KEY`, `DESX`, `AES_128`, `AES_192`und `AES_256`. Hinweis: Zum Ändern dieser Eigenschaft muss sich die Katalogdatenbank im Einzelbenutzermodus befinden.|
|**IS_SCALEOUT_ENABLED**|Wenn der Wert `True` lautet, wird das SSIS Scale Out-Feature aktiviert. Wenn Sie Scale Out nicht aktiviert haben, kann diese Eigenschaft nicht in der Sicht angezeigt werden.|
|**MAX_PROJECT_VERSIONS**|Die Anzahl von neuen Projektversionen, die für ein einzelnes Projekt beibehalten werden. Wenn Versionscleanup aktiviert ist, werden frühere Versionen, die diese Anzahl überschreiten, gelöscht.|  
|**OPERATION_CLEANUP_ENABLED**|Wenn der Wert `TRUE`ist, werden Vorgangsdetails und Vorgangsmeldungen, die älter als **RETENTION_WINDOW** (Tage) sind, aus dem Katalog gelöscht. Wenn der Wert `FALSE`ist, werden alle Vorgangsdetails und Vorgangsmeldungen im Katalog gespeichert. Hinweis: Das Vorgangscleanup erfolgt durch einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Auftrag.|  
|**RETENTION_WINDOW**|Die Anzahl der Tage, für die Vorgangsdetails und Vorgangsmeldungen im Katalog gespeichert werden. Wenn der Wert `-1`lautet, ist die Beibehaltungsdauer unendlich. Hinweis: Wenn kein Cleanup erfolgen soll, legen Sie **OPERATION_CLEANUP_ENABLED** auf **FALSE** fest.|
|**SCHEMA_BUILD**|Die Buildnummer des SSISDB-Katalogdatenbankschemas. Diese Nummer ändert sich, wenn Sie der SSISDB-Katalog erstellt oder aktualisiert wird.|
|**SCHEMA_VERSION**|Die Hauptversionsnummer des SSISDB-Katalogdatenbankschemas. Diese Nummer ändert sich, wenn Sie der SSISDB-Katalog erstellt oder ein Upgrade durchgeführt wird.|
|**VALIDATION_TIMEOUT**|Überprüfungen werden beendet, wenn sie nicht innerhalb der von dieser Eigenschaft angegebenen Anzahl von Sekunden abgeschlossen werden.|  
|**SERVER_CUSTOMIZED_LOGGING_LEVEL**|Der benutzerdefinierte Standardprotokolliergrad für den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server. Wenn Sie keine benutzerdefinierte Protokolliergrade erstellt haben, kann diese Eigenschaft nicht in der Sicht angezeigt werden.|
|**SERVER_LOGGING_LEVEL**|Der Standardprotokolliergrad für den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server.|
|**SERVER_OPERATION_ENCRYPTION_LEVEL**|Wenn der Wert „1“ (`PER_EXECUTION`) lautet, werden für jede *Ausführung* das Zertifikat und der symmetrische Schlüssel erstellt, die zum Schutz von sensiblen Ausführungsparameters und -protokollen verwendet werden. Wenn der Wert „2“ (`PER_PROJECT`) lautet, werden das Zertifikat und der symmetrische Schlüssel jeweils einmal für jedes *Projekt* erstellt. Weitere Informationen zu dieser Eigenschaft finden Sie unter den Hinweisen für die gespeicherte SSIS-Prozedur [catalog.cleanup_server_log](../system-stored-procedures/catalog-cleanup-server-log.md#remarks).|
|**VERSION_CLEANUP_ENABLED**|Wenn der Wert `TRUE`ist, wird nur die von **MAX_PROJECT_VERSIONS** angegebene Anzahl von Projektversionen im Katalog gespeichert, und alle anderen Projektversionen werden gelöscht. Wenn der Wert **FALSE** ist, werden alle Projektversionen im Katalog gespeichert. Hinweis: Das Vorgangscleanup erfolgt durch einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Auftrag.|
|||
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
  
