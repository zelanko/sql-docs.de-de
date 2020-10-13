---
description: Bewertungsbericht (accesstosql)
title: Bewertungsbericht (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 6c747f50c9216626e710318175cf5e53a0624d7a
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987656"
---
# <a name="assessment-report-accesstosql"></a>Bewertungsbericht (accesstosql)
Im Fenster Bewertungsbericht werden die Ergebnisse der Konvertierung von Datenbankobjekten in die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntax angezeigt. Außerdem können Sie die Komplexität und die Kosten ihrer Migrationsprojekte schätzen.  
  
Zum Erstellen eines Bewertungsberichts wählen Sie zu konvertierende Objekte im quellmetadatenexplorer aus, klicken Sie mit der rechten Maustaste auf **Datenbanken**, und wählen Sie dann **Bericht erstellen**aus. Sie können diesen Bericht auch nach dem Konvertieren von Schemas automatisch anzeigen. Der Berichts Name wird jedoch als Konvertierungs Bericht verwendet. Weitere Informationen finden Sie unter [Projekteinstellungen (GUI) (SSMA Common)](../sybase/project-settings-gui-sybasetosql.md).  
  
## <a name="options"></a>Tastatur  
**Explorer-Bereich**  
Enthält eine Hierarchie von Objekten im Bewertungsbericht. Erweitern Sie Ordner, um einzelne Objekte und unter Komponenten anzuzeigen. Wenn Sie auf eine Kategorie oder ein Objekt klicken, werden die Konvertierungsstatistiken für diese Kategorie oder dieses Objekt im Detailbereich angezeigt.  
  
**Detailbereich**  
Zeigt Konvertierungsstatistiken oder Fehler-und Warnmeldungen für das ausgewählte Objekt an. Wenn z. b. der Ordner Tabellen ausgewählt ist, zeigt der Bereich Details die Anzahl von Fremdschlüsseln, Indizes, primär Schlüsseln und Tabellen an, die konvertiert wurden.  
  
**Meldungsbereich**  
Zeigt die Fehler, Warnungen und Informationsmeldungen an, die beim Erstellen des Bewertungsberichts generiert wurden. Nachrichten werden nach Zahl gruppiert.  
  
Um die Nachrichten Details anzuzeigen, klicken Sie entweder auf **Fehler**, **Warnungen**oder **Meldungen**, und erweitern Sie dann eine Meldung. SSMA zeigt die Liste der Objekte an, die diesen Fehler aufweisen. Klicken Sie auf ein Objekt, um alle Konvertierungs Details für das Objekt anzuzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Referenz zur Benutzeroberfläche (Zugriff)](./user-interface-reference-accesstosql.md)  
