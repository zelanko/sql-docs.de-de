---
title: Assessment Report (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
caps.latest.revision: 14
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0881a10fa739b6a6539c12af6f29c78934c315a9
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "40394035"
---
# <a name="assessment-report-accesstosql"></a>Assessment Report (AccessToSQL)
Die Fenster "Assessment Report" zeigt die Ergebnisse der Konvertierung von Datenbankobjekten zu [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, und kann ebenfalls dazu beitragen, die Sie schätzen, die Komplexität und Kosten für Ihren Migrationsprojekten.  
  
Erstellen Sie ein Bewertungsbericht, Objekte gleichzeitig auszuwählen, für die Konvertierung in der Quelle Metadaten-Explorer mit der rechten Maustaste **Datenbanken**, und wählen Sie dann **Bericht erstellen**. Sie können in diesem Bericht auch automatisch anzeigen, nachdem Sie Schemas konvertieren. Allerdings werden den Namen des Berichts Konvertierungsbericht. Weitere Informationen finden Sie unter [Project Settings (GUI) (häufig SSMA)](http://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
## <a name="options"></a>Tastatur  
**Explorer-Bereich**  
Eine Hierarchie von Objekten in der Bewertungsbericht enthält. Erweitern Sie die Ordner, um die einzelnen Objekte und Unterkomponenten anzeigen. Wenn Sie eine Kategorie oder ein Objekt klicken, werden die Konvertierung von Statistiken für diese Kategorie oder das Objekt im Detailbereich angezeigt.  
  
**Detailbereich**  
Zeigt die Konvertierung Statistiken oder Fehler und Warnungen-Nachrichten für das ausgewählte Objekt. Z. B. wenn der Ordner "Tabellen" ausgewählt ist, zeigt im Detailbereich die Anzahl der Fremdschlüssel, Indizes, Primärschlüssel und Tabellen, die konvertiert wurden.  
  
**Meldungsbereich**  
Zeigt die Fehler, Warnungen und informationsmeldungen, die generiert wurden, bei der der Bewertungsbericht erstellt wurde. Nachrichten werden nach Anzahl gruppiert.  
  
Um die Details anzuzeigen, klicken Sie entweder **Fehler**, **Warnungen**, oder **Nachrichten**, und erweitern Sie dann eine Nachricht. SSMA wird die Liste der Objekte angezeigt, die diesen Fehler aufweisen. Klicken Sie auf ein Objekt, um alle Konvertierungsdetails für das Objekt anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
[Benutzer-Schnittstelle Reference(Access)](http://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
