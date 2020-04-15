---
title: Importieren von Visual FoxPro-Daten in Microsoft Access | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90ac16bbdbaf7f4dd29e14e66cf5b9dc666057f4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302447"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Importieren von Visual FoxPro-Daten in Microsoft Access
Sie können in einer Visual FoxPro-Datenbank gespeicherte Daten mithilfe der Option Importieren in eine Microsoft Access-Datenbank importieren.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>So importieren Sie Visual FoxPro-Daten in eine Microsoft Access-Datenbank  
  
1.  Öffnen Sie eine Microsoft Access-Datenbank.  
  
2.  Wählen Sie im Menü Datei externe Daten abrufen und dann Importieren aus.  
  
3.  Wählen Sie im Dialogfeld Import odBC-Datenbanken in der Liste Dateien vom Typ aus.  
  
4.  Wählen Sie im Dialogfeld SQL-Datenquellen die Visual FoxPro-Datenquelle aus, die eine Verbindung zu den FoxPro-Daten herstellt, die Sie abfragen möchten, und klicken Sie auf OK.  
  
5.  Wählen Sie im Dialogfeld Objekte importieren eine oder mehrere Tabellen aus, die Sie importieren möchten, und klicken Sie auf OK. Die Namen der importierten Visual FoxPro-Tabellen werden auf der Registerkarte Tabellen der Microsoft Access-Datenbank angezeigt.  
  
 Sie können jetzt Microsoft Access verwenden, um die Daten in den importierten Visual FoxPro-Tabellen zu bearbeiten. Die importierten Daten sind eine Momentaufnahme der in Visual FoxPro gespeicherten Daten. Änderungen, die Sie an importierten Daten vornehmen, werden nicht an die Visual FoxPro-Datenquelle zurückgesendet.  
  
 Wenn Sie Änderungen in Microsoft Access vornehmen möchten, um die Daten in der Visual FoxPro-Datenquelle zu ändern, finden Sie weitere Informationen unter [Abfragen und Aktualisieren von Visual FoxPro-Daten von Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
