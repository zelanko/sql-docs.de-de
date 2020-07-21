---
title: MSSQLSERVER_8525 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e7996bffe4fcea7f29d43d04d63e2b4b37b2241
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86550885"
---
# <a name="mssqlserver_8525"></a>MSSQLSERVER_8525
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8525|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Die verteilte Transaktion wurde abgeschlossen. Tragen Sie diese Sitzung in eine neue Transaktion oder in die NULL-Transaktion ein.|  
  
## <a name="explanation"></a>Erklärung  
 Für das Programmiermodell für die Verwendung des Distributed Transaction Coordinators mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sind Anwendungen zum expliziten Eintragen in und Austragen aus einer verteilten Transaktion erforderlich.  
  
 Dieser Fehler tritt auf, wenn die folgenden vier Bedingungen erfüllt sind:  
  
-   Die Anwendung wurde in eine verteilte Transaktion eingetragen.  
  
-   Die Transaktion wurde aus irgendeinem Grund beendet (durch einen Commit oder ein Rollback).  
  
-   Die Benutzeranwendung wurde nicht explizit aus einer verteilten Transaktion ausgetragen oder explizit in eine neue verteilte Transaktion eingetragen.  
  
-   Die Anwendung versucht jeden anderen Transaktionsvorgang als das Austragen aus einer vorhandenen verteilten Transaktion oder das Eintragen in eine neue verteilte Transaktion, z. B. das Ausgeben einer Abfrage oder das Starten einer lokalen Transaktion.  
  
 Der Fehlerzustand 1 wird verwendet, wenn die Anwendung einen Vorgang ausführt, mit dem lokale Transaktionen erstellt werden, und Status 2 wird verwendet, wenn die Anwendung versucht, eine Eintragung in eine gebundene Sitzung vorzunehmen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Nachdem eine Anwendung eine Eintragung in eine verteilte Transaktion vorgenommen hat, muss sich die Anwendung explizit aus der verteilten Transaktion austragen oder sich in eine andere verteilte Transaktion eintragen. Damit wird implizit ein Austritt aus einer vorherigen eingetragenen Transaktion vorgenommen. Informationen dazu, wie die genaue Syntax aus einer verteilten Transaktion ausgetragen oder in eine verteilte Transaktion eingetragen wird, finden Sie im Handbuch zur Programmierschnittstelle für die Anwendung.  
  
  
