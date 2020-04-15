---
title: SQLTables (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5467fc8c1717d5ceb548b3950a0894fd2a1b4499
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299283"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Ebene 1  
  
 Gibt die Liste der Tabellennamen zurück, die durch den Parameter in der **SQLTables-Anweisung** angegeben sind. Wenn kein Parameter angegeben ist, werden die in der aktuellen Datenquelle gespeicherten Tabellennamen zurückgegeben. Der Treiber gibt die Informationen als Ergebnissatz zurück.  
  
 Enumerationstypaufrufe erhalten keinen Ergebnissatzeintrag für Remoteansichten oder lokale parametrisierte Ansichten. Ein Aufruf von **SQLTables** mit einem eindeutigen Tabellennamensbezeichner findet jedoch eine Übereinstimmung für eine solche Ansicht, wenn diese Ansicht vorhanden ist. Auf diese Weise kann die API verwendet werden, um vor dem Erstellen einer neuen Tabelle nach Namenskonflikten zu suchen.  
  
> [!NOTE]  
>  Der Visual FoxPro ODBC-Treiber unterscheidet zwischen [Datenbanktabellen](../../odbc/microsoft/visual-foxpro-terminology.md) und [freien Tabellen,](../../odbc/microsoft/visual-foxpro-terminology.md)auch wenn beide Tabellentypen im selben Verzeichnis auf Ihrem System gespeichert werden. Wenn es sich bei ihrer Datenquelle um ein Verzeichnis kostenloser Tabellen handelt, katalogisiert oder gibt der Visual FoxPro ODBC-Treiber die Namen von Tabellen, die einer Datenbank zugeordnet sind, nicht zurück.  
  
 Weitere Informationen finden Sie unter [SQLTables](../../odbc/reference/syntax/sqltables-function.md) in der *ODBC-Programmiererreferenz*.
