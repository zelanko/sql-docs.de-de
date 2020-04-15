---
title: Erstellen von Adressetiketten in Microsoft Word mithilfe von Visual FoxPro-Daten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data [ODBC], mailing labels
- Visual FoxPro data [ODBC], Word
- mailing labels [ODBC]
- Visual FoxPro ODBC driver [ODBC], Word
- FoxPro ODBC driver [ODBC], word
ms.assetid: c901b60c-9f84-407a-b3d1-b4d301a71370
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3ca6c729cfa988e2560192d705bc24e9e7b4fa1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280800"
---
# <a name="creating-mailing-labels-in-microsoft-word-using-visual-foxpro-data"></a>Erstellen von Adressetiketten in Microsoft Word mithilfe von Visual FoxPro-Daten
Sie können Visual FoxPro-Daten in einem Microsoft Word für Windows 95- oder Windows 98-Dokument verwenden. Sie können z. B. Adressetiketten aus den In einer Visual FoxPro-Tabelle gespeicherten Kundeninformationen erstellen.  
  
### <a name="to-create-mailing-labels"></a>So erstellen Sie Adressetiketten  
  
1.  Erstellen Sie in Microsoft Word ein neues leeres Dokument.  
  
2.  Wählen Sie im Menü Extras die Option Seriendruck aus.  
  
3.  Wählen Sie im Seriendruck-Hilfsgerät die Option Erstellen und dann Die Option Adressetiketten aus.  
  
4.  Wählen Sie unter Hauptdokument aktives Fenster aus.  
  
5.  Wählen Sie unter Datenquelle die Option Daten abrufen und dann Open Data Source aus.  
  
6.  Wählen Sie im Dialogfeld Quellquelle öffnen die Option MS Query aus.  
  
7.  Wählen Sie im Dialogfeld Datenquelle auswählen eine Visual FoxPro-Datenquelle aus, und klicken Sie dann auf Verwenden.  
  
8.  Wenn die Datenbank, auf die von der Datenquelle zugegriffen wird, Tabellen enthält, wählen Sie im Dialogfeld Tabellen hinzufügen eine Tabelle aus. Microsoft Query zeigt die hinzugefügte Tabelle in der oberen Hälfte des Abfrage-Designers an.  
  
9. Wählen Sie Felder für Ihre Abfrage aus, indem Sie sie aus der Tabelle in die untere Hälfte des Designers ziehen.  
  
10. Wählen Sie im Menü Datei die Option Daten an Microsoft Word zurückgeben aus. Microsoft Query wird geschlossen, und die ausgewählten Daten können in Ihrem Seriendruckdokument verwendet werden.  
  
11. Wählen Sie unter Hauptdokument Setup aus.  
  
12. Wählen Sie im Dialogfeld Beschriftungsoptionen die gewünschten Drucker- und Beschriftungsinformationen aus, und klicken Sie dann auf OK.  
  
13. Wählen Sie im Dialogfeld Etiketten erstellen die Felder aus, die Sie auf den Adressetiketten drucken möchten, und klicken Sie dann auf OK.  
  
14. Klicken Sie im Seriendruck-Hilfegerät unter Zusammenführen der Daten mit dem Dokument auf Zusammenführen.  
  
15. Wählen Sie im Dialogfeld Zusammenführen die gewünschten Optionen aus, und klicken Sie dann auf Zusammenführen.
