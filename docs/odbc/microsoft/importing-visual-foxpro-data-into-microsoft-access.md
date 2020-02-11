---
title: Importieren von Visual FoxPro-Daten in Microsoft Access | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 557b5505b9eb6a15080a7d0495df2e63aefd2d76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085545"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Importieren von Visual FoxPro-Daten in Microsoft Access
Sie können Daten, die in einer Visual FoxPro-Datenbank gespeichert sind, mithilfe der Import-Option in eine Microsoft Access-Datenbank importieren.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>So importieren Sie Visual FoxPro-Daten in eine Microsoft Access-Datenbank  
  
1.  Öffnen Sie eine Microsoft Access-Datenbank.  
  
2.  Wählen Sie im Menü Datei die Option externe Daten importieren und dann importieren aus.  
  
3.  Wählen Sie im Dialogfeld Importieren in der Liste Dateityp die Option ODBC-Datenbanken aus.  
  
4.  Wählen Sie im Dialogfeld SQL-Datenquellen die Visual FoxPro-Datenquelle aus, die eine Verbindung mit den FoxPro-Daten herstellt, die Sie Abfragen möchten, und klicken Sie auf OK.  
  
5.  Wählen Sie im Dialogfeld Objekte importieren mindestens eine Tabelle aus, die Sie importieren möchten, und klicken Sie auf OK. Die Namen der importierten Visual FoxPro-Tabellen werden auf der Registerkarte Tabellen der Microsoft Access-Datenbank angezeigt.  
  
 Sie können jetzt Microsoft Access verwenden, um die Daten in den importierten Visual FoxPro-Tabellen zu manipulieren. Bei den importierten Daten handelt es sich um eine Momentaufnahme der in Visual FoxPro gespeicherten Daten. Änderungen, die Sie an importierten Daten vornehmen, werden nicht zurück an die Visual FoxPro-Datenquelle gesendet.  
  
 Wenn Sie Änderungen vornehmen möchten, die Sie in Microsoft Access vornehmen, um die Daten in der Visual FoxPro-Datenquelle zu ändern, finden Sie weitere [Informationen Unterabfragen und Aktualisieren von Visual FoxPro-Daten aus Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
