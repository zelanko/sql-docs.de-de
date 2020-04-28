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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f11b49ed099ba29d0e7e013af99a8ad96ca6825c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292870"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Abfragen und Aktualisieren von Visual FoxPro-Daten aus Microsoft Access
Sie können Daten, die in einer Visual FoxPro-Datenbank gespeichert sind, aus einer Microsoft Access-Datenbank mithilfe der Link Tabellen-Option Abfragen und aktualisieren.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>So verknüpfen Sie eine Visual FoxPro-Datenbank mit einer Microsoft Access-Datenbank  
  
1.  Öffnen Sie eine Microsoft Access-Datenbank.  
  
2.  Klicken Sie auf der Registerkarte Tabellen auf neu.  
  
3.  Wählen Sie im Dialogfeld neue Tabelle die Option Link Tabelle aus, und klicken Sie auf OK.  
  
4.  Wählen Sie im Dialog Feld Link in der Liste Dateityp die Option ODBC-Datenbank aus.  
  
5.  Wählen Sie im Dialogfeld SQL-Datenquellen die Datenquelle aus, die eine Verbindung mit den Visual FoxPro-Daten herstellt, die Sie Abfragen möchten, und klicken Sie auf OK.  
  
6.  Wählen Sie im Dialogfeld Tabellen verknüpfen die Tabellen aus, die Sie Abfragen und aktualisieren möchten, und klicken Sie auf OK. Die verknüpften Visual FoxPro-Tabellen werden auf der Registerkarte Tabellen der Microsoft Access-Datenbank angezeigt.  
  
 Sie können jetzt Microsoft Access verwenden, um Daten in den verknüpften Visual FoxPro-Tabellen abzufragen und zu aktualisieren. Änderungen, die Sie an verknüpften Daten vornehmen, werden zurück an die Visual FoxPro-Datenquelle gesendet.  
  
 Wenn Sie nicht möchten, dass Änderungen, die Sie in Microsoft Access vornehmen, die Daten in der Visual FoxPro-Datenquelle beeinflussen, finden Sie weitere Informationen unter [Importieren von Visual FoxPro-Daten in Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
