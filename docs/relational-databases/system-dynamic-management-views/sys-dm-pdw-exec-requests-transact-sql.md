---
title: sys.dm_pdw_exec_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4f4ebcbf84da7d899b4d4cbd861cfb2ae3f75863
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087560"
---
# <a name="sysdm_pdw_exec_requests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen zu allen Anforderungen, [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]die derzeit oder kürzlich in aktiv sind. Es listet eine Zeile pro Anforderung/Abfrage auf.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Schlüssel für diese Ansicht. Eindeutige numerische ID, die der Anforderung zugeordnet ist.|Einzigartig für alle Anforderungen im System.|  
|session_id|**nvarchar(32)**|Eindeutige numerische ID, die der Sitzung zugeordnet ist, in der diese Abfrage ausgeführt wurde. Siehe [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|status|**nvarchar(32)**|Aktueller Status der Anforderung.|'Running', 'Suspended', 'Completed', 'Canceled', 'Failed'.|  
|submit_time|**datetime**|Zeitpunkt, zu dem der Antrag zur Ausführung übermittelt wurde.|Gültige **Datumszeit** kleiner oder gleich der aktuellen Uhrzeit und start_time.|  
|start_time|**datetime**|Zeitpunkt, zu dem die Anforderungsausführung gestartet wurde.|NULL für Anforderungen in die Warteschlange; andernfalls die **gültigkeitsdatumszeit** kleiner oder gleich der aktuellen Zeit.|  
|end_compile_time|**datetime**|Zeitpunkt, zu dem das Modul die Kompilierung der Anforderung abgeschlossen hat.|NULL für Anforderungen, die noch nicht kompiliert wurden; andernfalls eine gültige **Datumszeit,** die kleiner als start_time und kleiner oder gleich der aktuellen Zeit ist.|
|end_time|**datetime**|Zeitpunkt, zu dem die Anforderungsausführung abgeschlossen, fehlgeschlagen oder abgebrochen wurde.|Null für in die Warteschlange gestellte oder aktive Anforderungen; andernfalls eine gültige **Datumszeit** kleiner oder gleich der aktuellen Zeit.|  
|total_elapsed_time|**int**|Die Ausführungszeit seit dem Start der Anforderung in Millisekunden verstrichen.|Zwischen 0 und dem Unterschied zwischen start_time und end_time.</br></br> Wenn total_elapsed_time den Maximalwert für eine ganze Zahl überschreitet, ist total_elapsed_time weiterhin der Maximalwert. Diese Bedingung generiert die Warnung "Der Maximalwert wurde überschritten."</br></br> Der Maximalwert in Millisekunden entspricht 24,8 Tagen.|  
|label|**nvarchar(255)**|Optionale Beschriftungszeichenfolge, die einigen SELECT-Abfrageanweisungen zugeordnet ist.|Jede Zeichenfolge, die 'a-z','A-Z','0-9','_' enthält.|  
|error_id|**nvarchar(36)**|Eindeutige ID des Fehlers, der der Anforderung zugeordnet ist, falls vorhanden.|Siehe [sys.dm_pdw_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); auf NULL gesetzt, wenn kein Fehler aufgetreten ist.|  
|database_id|**int**|Bezeichner der Datenbank, die vom expliziten Kontext verwendet wird (z. B. USE DB_X).|Siehe ID in [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|command|**nvarchar(4000)**|Enthält den vollständigen Text der Anforderung, wie er vom Benutzer übermittelt wurde.|Jeder gültige Abfrage- oder Anforderungstext. Abfragen, die länger als 4000 Byte sind, werden abgeschnitten.|  
|resource_class|**nvarchar(20)**|Die Arbeitsauslastungsgruppe, die für diese Anforderung verwendet wird. |Statische Ressourcenklassen</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80</br>            </br>Dynamische Ressourcenklassen</br>SmallRC</br>MediumRC</br>LargeRC</br>XLargeRC|
|importance|**nvarchar(128)**|Die Wichtigkeit, die die Anforderung festlegt, die ausgeführt wird.  Dies ist die relative Bedeutung einer Anforderung in dieser Workloadgruppe und über Workloadgruppen hinweg für freigegebene Ressourcen.  Die in der Klassifier angegebene Wichtigkeit überschreibt die Wichtigkeitseinstellung der Workloadgruppe.</br>Gilt für: Azure SQL Data Warehouse|NULL</br>niedrig</br>below_normal</br>normal (Standard)</br>above_normal</br>high|
|group_name|**sysname** |Bei Anforderungen, die Ressourcen verwenden, ist group_name der Name der Arbeitsauslastungsgruppe, unter der die Anforderung ausgeführt wird.  Wenn die Anforderung keine Ressourcen verwendet, ist group_name null.</br>Gilt für: Azure SQL Data Warehouse|
|classifier_name|**sysname**|Für Anforderungen, die Ressourcen verwenden, Der Name des Klassifiierers, der zum Zuweisen von Ressourcen und wichtig verwendet wird.||
|resource_allocation_percentage|**dezimal(5,2)**|Der prozentuale Betrag der Ressourcen, die der Anforderung zugeordnet sind.</br>Gilt für: Azure SQL Data Warehouse|
|result_cache_hit|**Hexadezimale**|Gibt an, ob eine abgeschlossene Abfrage den Ergebnissatzcache verwendet hat.  </br>Gilt für: Azure SQL Data Warehouse| 1 = Ergebnissatz-Cache-Treffer </br> 0 = Ergebnissatz-Cache-Fehler </br> Negative Werte = Gründe, warum die Zwischenspeicherung von Resultsets nicht verwendet wurde.  Weitere Informationen finden Sie im Abschnitt "Bemerkungen".|
||||
  
## <a name="remarks"></a>Bemerkungen 
 Informationen zu den maximalen Zeilen, die von dieser Ansicht beibehalten werden, finden Sie im Abschnitt Metadaten im Thema [Kapazitätsgrenzen.](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)

 Die result_cache_hit ist eine Bitmaske für die Verwendung des Ergebnissatzcache einer Abfrage.  Diese Spalte kann die [| (Bitweise ODER)](../../t-sql/language-elements/bitwise-or-transact-sql.md) Produkt eines oder mehrerer dieser Werte:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Ergebnissatz-Cache-Treffer|  
|-**0x00**|Ergebnissatz-Cache-Fehler|  
|-**0x01**|Die Zwischenspeicherung von Resultsets ist in der Datenbank deaktiviert.|  
|-**0x02**|Die Zwischenspeicherung des Ergebnissatzes ist für die Sitzung deaktiviert. | 
|-**0x04**|Die Zwischenspeicherung von Resultsets ist deaktiviert, da keine Datenquellen für die Abfrage vorhanden sind.|  
|-**0x08**|Das Zwischenspeichern von Resultsets ist aufgrund von Sicherheitsprädikaten auf Zeilenebene deaktiviert.|  
|-**0x10**|Die Zwischenspeicherung von Resultsets ist aufgrund der Verwendung von Systemtabelle, temporärer Tabelle oder externer Tabelle in der Abfrage deaktiviert.|  
|-**0x20**|Die Zwischenspeicherung von Resultsets ist deaktiviert, da die Abfrage Laufzeitkonstanten, benutzerdefinierte Funktionen oder nicht deterministische Funktionen enthält.|  
|-**0x40**|Die Zwischenspeicherung des Ergebnissatzes ist aufgrund der geschätzten Größe des Resultsets >10 GB deaktiviert.|  
|-**0x80**|Die Zwischenspeicherung des Resultsets ist deaktiviert, da das Resultset Zeilen mit großer Größe (>64 kb) enthält.|  
  
## <a name="permissions"></a>Berechtigungen

 Erfordert die VIEW SERVER STATE-Berechtigung.  
  
## <a name="security"></a>Sicherheit

 sys.dm_pdw_exec_requests filtert Abfrageergebnisse nicht nach datenbankspezifischen Berechtigungen. Anmeldungen mit VIEW SERVER STATE-Berechtigung können Ergebnisabfrageergebnisse für alle Datenbanken erhalten  
  
>[!WARNING]  
>Ein Angreifer kann sys.dm_pdw_exec_requests verwenden, um Informationen zu bestimmten Datenbankobjekten abzurufen, indem er einfach über VIEW SERVER STATE-Berechtigungen verfügt und keine datenbankspezifische Berechtigung hat.  
  
## <a name="see-also"></a>Weitere Informationen

 [SQL Data Warehouse und Parallel Data Warehouse Dynamic Management Views &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)
