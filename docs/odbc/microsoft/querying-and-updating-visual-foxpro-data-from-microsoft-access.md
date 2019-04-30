---
title: Abfragen und Aktualisieren von Visual FoxPro-Daten aus Microsoft Access | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1097e03c414d919a606ffd21ae50ffddf51173b7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316761"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Abfragen und Aktualisieren von Visual FoxPro-Daten aus Microsoft Access
Sie können Abfragen und Aktualisieren von Daten in einer Visual FoxPro-Datenbank aus einer Microsoft Access-Datenbank mithilfe der Option Linktabelle gespeichert.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Beim Verknüpfen von einer Visual FoxPro-Datenbank mit einer Microsoft Access-Datenbank  
  
1.  Öffnen Sie eine Microsoft Access-Datenbank.  
  
2.  Klicken Sie auf "Neu", auf die Registerkarte "Tabellen".  
  
3.  Klicken Sie im Dialogfeld "neue Tabelle" Wählen Sie Linktabelle aus, und klicken Sie auf OK.  
  
4.  Wählen Sie in das Link-Dialogfeld ODBC-Datenbank in der Liste ein.  
  
5.  Wählen Sie im Dialogfeld SQL-Datenquellen die Datenquelle, die eine Verbindung mit der Visual FoxPro-Daten, die Sie verwenden möchten herstellt, Abfragen, und klicken Sie auf OK.  
  
6.  Wählen Sie im Dialogfeld Verknüpfungstabellen die Tabellen, die Sie verwenden möchten, Abfragen und aktualisieren, und klicken Sie auf OK. Die verknüpften Visual FoxPro-Tabellen werden in der Registerkarte "Tabellen" der Microsoft Access-Datenbank angezeigt.  
  
 Sie können nun Microsoft Access verwenden, zum Abfragen und Aktualisieren von Daten in der verknüpften Visual FoxPro-Tabellen. Änderungen an verknüpften Daten werden in der Visual FoxPro-Datenquelle gesendet.  
  
 Wenn Sie nicht, dass Änderungen möchten Sie vornehmen, in Microsoft Access zum Einfluss auf die Daten in der Visual FoxPro-Datenquelle finden Sie unter [von Visual FoxPro-Daten in Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
