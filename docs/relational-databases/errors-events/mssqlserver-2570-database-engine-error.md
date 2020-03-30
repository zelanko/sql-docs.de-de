---
title: MSSQLSERVER_2570 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 63adadd3dda40dc520e2152eab1a461dfe69958a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68023053"
---
# <a name="mssqlserver_2570"></a>MSSQLSERVER_2570
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2570|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|Meldungstext|Seite P_ID, Slot S_ID in Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (TYPE-Typ). Der Wert der COLUMN_NAME-Spalte liegt für den "DATATYPE"-Datentyp außerhalb des gültigen Bereichs. Aktualisieren Sie die Spalte auf einen gültigen Wert.|  
  
## <a name="explanation"></a>Erklärung  
Der Spaltenwert, der in der angegebenen Spalte enthalten ist, liegt außerhalb des Bereichs der möglichen Werte für den Spaltendatentyp.  
  
## <a name="user-action"></a>Benutzeraktion  
Der Fehler kann nicht behoben werden. Aktualisieren Sie die Spalte auf einen Wert innerhalb des Bereichs für den Datentyp der Spalte, und führen Sie den Befehl erneut aus.  Weitere Informationen finden Sie im KB-Artikel [923247](https://support.microsoft.com/kb/923247).  
  
## <a name="see-also"></a>Weitere Informationen  
[UPDATE &#40;Transact-SQL&#41;](~/t-sql/queries/update-transact-sql.md)  
[Datentypen &#40;Transact-SQL&#41;](~/t-sql/data-types/data-types-transact-sql.md)  
  
