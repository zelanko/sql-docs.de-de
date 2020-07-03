---
title: sysssislog (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtslog90_TSQL
- sysdtslog90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssislog system table
ms.assetid: 7fa288a1-81e3-42a0-82f6-8a59019693d0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 264f6495c12a350983af22c1bef325278238a514
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889267"
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jeden Protokollierungseintrag, der von Paketen oder deren Tasks und Containern zur Laufzeit generiert wird. Diese Tabelle wird in der msdb-Datenbank erstellt, wenn Sie installieren [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Wenn Sie die Protokollierung so konfigurieren, dass eine andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank protokolliert wird, wird in der angegebenen Datenbank eine sysssislog-Tabelle mit diesem Format erstellt.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]schreibt Protokollierungs Einträge **nur** in diese Tabelle, wenn Pakete den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokoll Anbieter verwenden.  
  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|id|**int**|Der eindeutige Bezeichner des Protokollierungseintrags.|  
|event|**sysname**|Der Name des Ereignisses, das den Protokollierungseintrag generiert hat.|  
|computer|**nvarchar**|Der Computer, auf dem das Paket ausgeführt wurde, als der Protokollierungseintrag generiert wurde.|  
|Operator|**nvarchar**|Der Benutzername der Person, die das Paket ausgeführt hat, das den Protokollierungseintrag generiert hat.|  
|source|**nvarchar**|Der Name der ausführbaren Datei im Paket, das den Protokolleintrag generiert hat.|  
|sourceid|**uniqueidentifier**|Die GUID der ausführbaren Datei im Paket, das den Protokolleintrag generiert hat.|  
|executionid|**uniqueidentifier**|GUID der Ausführungsinstanz der ausführbaren Datei, die den Protokollierungseintrag generiert hat.|  
|starttime|**datetime**|Der Zeitpunkt, zu dem die Paketausführung gestartet wurde.|  
|endtime|**datetime**|Der Zeitpunkt, zu dem das Paket abgeschlossen wurde.<br /><br /> Diese Funktion ist nicht implementiert. Der Wert in der Spalte endtime entspricht immer dem Wert in der Spalte starttime.|  
|datacode|**int**|Ein optionaler ganzzahliger Wert, der in der Regel das Ergebnis der Ausführung des Containers oder der Task angibt.|  
|databytes|**Bild**|Ein optionales Bytearray, das weitere Informationen enthält.|  
|message|**nvarchar**|Eine Beschreibung des Ereignisses sowie die mit dem Ereignis verknüpften Informationen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Protokollierung &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
