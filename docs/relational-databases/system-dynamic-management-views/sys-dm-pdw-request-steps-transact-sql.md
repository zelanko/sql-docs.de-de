---
description: sys.dm_pdw_request_steps (Transact-SQL)
title: sys.dm_pdw_request_steps (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/28/2020
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 839a1d906fcd7b6a4a980a7381b4f5fcdcf10d5d
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97644038"
---
# <a name="sysdm_pdw_request_steps-transact-sql"></a>sys.dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält Informationen zu allen Schritten, die eine bestimmte Anforderung oder Abfrage in verfassen [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] . Es wird eine Zeile pro Abfrage Schritt aufgelistet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|request_id und step_index bilden den Schlüssel für diese Ansicht.<br /><br /> Eindeutige numerische ID, die der Anforderung zugeordnet ist.|Weitere Informationen finden Sie unter request_id in [sys.dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|request_id und step_index bilden den Schlüssel für diese Ansicht.<br /><br /> Die Position dieses Schritts in der Abfolge der Schritte, die die Anforderung bilden.|0 bis (n-1) für eine Anforderung mit n Schritten.|  
|plan_node_id|**int**|Die Knoten-ID, die der Operator-ID dieses Schritts im Ausführungsplan entspricht.|Keine|  
|operation_type|**nvarchar(35)**|Der Typ des Vorgangs, der durch diesen Schritt dargestellt wird.|**DMS-Abfrageplan Vorgänge:** "Returnoperation", "partitionmuveoperation", "muveoperation", "broadcastmuveoperation", "shufflemuveoperation", "trimmuveoperation", "copyoperation", "distributerepli-tablemuveoperation"<br /><br /> **SQL-Abfrageplan Vorgänge:** "Onoperation", "Remoteoperation"<br /><br /> **Andere Abfrageplan Vorgänge:** ' MetaDataCreateOperation ', ' randomidoperation '<br /><br /> **Externe Vorgänge für Lesevorgänge:** "Hadoopshuffleoperation", "hadooproundrobinoperation", "hadoopbroadcastoperation"<br /><br /> **Externe Vorgänge für MapReduce:** "Hadoopjoboperation", "hdfsdeleteoperation"<br /><br /> **Externe Vorgänge für Schreibvorgänge:** "Externalexportdistributedoperation", "externalexportreplialisiedoperation", "externalexportcontroloperation"<br /><br /> Weitere Informationen finden Sie unter "Grundlegendes zu Abfrage Plänen" in der [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] . <br /><br />  Ein Abfrageplan kann auch von den Datenbankeinstellungen beeinflusst werden.  Weitere Informationen finden Sie unter [ALTER DATABASE SET-Optionen](../../t-sql/statements/alter-database-transact-sql-set-options.md?bc=%252fazure%252fsql-data-warehouse%252fbreadcrumb%252ftoc.json&toc=%252fazure%252fsql-data-warehouse%252ftoc.json&view=azure-sqldw-latest&preserve-view=true) .|  
|distribution_type|**nvarchar(32)**|Verteilungstyp dieser Schritt wird durchlaufen.|"Allnodes", "alldistributionen", "allcomputenodes", "computenode", "Distribution", "subsetnodes", "subsetverteilungen", "nicht angegeben"|  
|location_type|**nvarchar(32)**|Gibt an, wo der Schritt ausgeführt wird.|"Compute", "Control", "DMS"|  
|status|**nvarchar(32)**|Status dieses Schritts.|Ausstehend, wird ausgeführt, abgeschlossen, Fehler, undofailed, Aktion abbrechen, abgebrochen, rückgängig gemacht, abgebrochen|  
|error_id|**nvarchar (36)**|Eindeutige ID des Fehlers, der diesem Schritt zugeordnet ist, sofern vorhanden.|Weitere Informationen finden Sie unter error_id [sys.dm_pdw_errors &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). NULL, wenn kein Fehler aufgetreten ist.|  
|start_time|**datetime**|Der Zeitpunkt, zu dem die Ausführung des Schritts gestartet wurde.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich end_compile_time der Abfrage, zu der dieser Schritt gehört. Weitere Informationen zu Abfragen finden Sie unter [sys.dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Der Zeitpunkt, zu dem dieser Schritt die Ausführung abgeschlossen hat, abgebrochen wurde oder fehlgeschlagen ist.|Kleiner oder gleich der aktuellen Zeit und größer oder gleich start_time. Auf NULL für Schritte festgelegt, die gerade ausgeführt werden oder in der Warteschlange stehen.|  
|total_elapsed_time|**int**|Gesamtzeit Spanne in Millisekunden, während der der Abfrage Schritt ausgeführt wurde.|Zwischen 0 und dem Unterschied zwischen end_time und start_time. 0 für Schritte in der Warteschlange.<br /><br /> Wenn total_elapsed_time den maximalen Wert für eine ganze Zahl überschreitet, ist total_elapsed_time weiterhin der Höchstwert. Mit dieser Bedingung wird die Warnung "der Höchstwert wurde überschritten" generiert.<br /><br /> Der maximale Wert in Millisekunden entspricht 24,8 Tagen.|  
|row_count|**bigint**|Die Gesamtanzahl der von dieser Anforderung geänderten oder zurückgegebenen Zeilen.|Die Anzahl der Zeilen, auf die sich der Schritt ausgewirkt hat.  Größer oder gleich 0 (null) für Daten Vorgangs Schritte.  -1 für die Schritte, die nicht für Daten ausgeführt werden.|  
|estimated_rows|**bigint**|Gesamtanzahl der Arbeits Zeilen, die während der Kompilierung der Abfrage berechnet wurden.|Die Anzahl der Zeilen, die durch den Schritt geschätzt werden.  Größer oder gleich 0 (null) für Daten Vorgangs Schritte.  -1 für die Schritte, die nicht für Daten ausgeführt werden.|  
|command|**nvarchar(4000)**|Enthält den vollständigen Text des Befehls dieses Schritts.|Eine beliebige gültige Anforderungs Zeichenfolge für einen Schritt. NULL, wenn der Vorgang vom Typ MetaDataCreateOperation ist. Wird abgeschnitten, wenn mehr als 4000 Zeichen enthalten sind.|  
  
 Informationen über die maximale Anzahl von Zeilen, die in dieser Sicht beibehalten werden, finden Sie im Abschnitt maximale System Sicht Werte im Abschnitt "minimal-und Maximalwerte" in der [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Azure Synapse Analytics und parallele Data Warehouse dynamische Verwaltungs Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
