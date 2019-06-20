---
title: RDS-Tutorial | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO]
ms.assetid: 6e3305a0-7bc7-40d1-9122-235c15d23ab2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3d1f328baf628e86c75abc9a452600e1f0e8cf88
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704255"
---
# <a name="rds-tutorial"></a>RDS-Tutorial
Dieses Tutorial veranschaulicht das Verwenden von RDS-Programmiermodell zum Abfragen und Aktualisieren einer Datenquelle. Zuerst beschreibt es die erforderlichen Schritte zum Ausführen dieser Aufgabe. Anschließend wird das Tutorial in Microsoft® Visual Basic Scripting Edition (mit ADO für die Windows Foundation Classes (ADO/WFC)) wiederholt.  
  
 In diesem Tutorial wird aus zwei Gründen in verschiedenen Sprachen codiert:  
  
-   Die Dokumentation für RDS geht davon aus, die Reader-Codes in Visual Basic. Dadurch wird die Dokumentation für Visual Basic-Programmierer praktisch, aber weniger nützlich für Programmierer, die andere Sprachen verwenden.  
  
-   Wenn Sie unsicher, eine bestimmte Funktion von RDS und man etwas von einer anderen Sprache möglicherweise können Sie Ihre Frage zu beheben, indem Sie suchen, die für die gleiche Funktion, die in einer anderen Sprache ausgedrückt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="how-the-tutorial-is-presented"></a>Wie im Tutorial dargestellt werden  
 Dieses Tutorial basiert auf dem RDS-Programmiermodell. Es wird jeder Schritt des Programmiermodells einzeln erläutert. Darüber hinaus veranschaulicht es jeden Schritt mit der ein Fragment des Visual Basic-Code.  
  
 Im Codebeispiel wird in anderen Sprachen mit minimalen Diskussion wiederholt. Jeder Schritt in einem Lernprogramm einer bestimmten Sprache wird in das Programmiermodell und die beschreibenden Tutorial mit dem entsprechenden Schritt markiert. Verwenden Sie die Anzahl der im Schritt zum Verweisen auf die Diskussion in diesem Tutorial beschreibenden.  
  
 Im folgenden Abschnitt wird angegeben, die RDS-Programmiermodell ist. Verwenden Sie es als eine Roadmap, wie Sie mit dem Tutorial fortfahren.  
  
## <a name="rds-programming-model-with-objects"></a>RDS-Programmiermodell mit Objekten  
  
-   Geben Sie das Programm auf dem Server aufgerufen werden, und rufen Sie eine Möglichkeit (Proxy) vom Client darauf verweisen.  
  
-   Serverprogramm aufrufen. Übergeben Sie Parameter, um die Server-Anwendung, die die Datenquelle und den Befehl, um das Problem identifiziert.  
  
-   Das Serverprogramm erhält eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt aus der Datenquelle, in der Regel mithilfe von ADO. Optional können die **Recordset** Objekt wird auf dem Server verarbeitet.  
  
-   Serverprogramm gibt zurück, die endgültige **Recordset** Objekt an die Clientanwendung.  
  
-   Auf dem Client die **Recordset** Objekt in ein Formular, das leicht von visuellen Steuerelementen verwendet werden, kann optional versetzt wird.  
  
-   Änderungen an der **Recordset** Objekt wieder an den Server gesendet und zum Aktualisieren der Datenquelle verwendet werden.  
  
 In diesem Tutorial enthält die folgenden Themen.  
  
-   [Schritt 1: Geben Sie eine Serverprogramm (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)  
  
-   [Schritt 2: Rufen Sie die Server-Anwendung (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)  
  
-   [Schritt 3: Server erhält ein Recordset (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)  
  
-   [Schritt 4: Server gibt das Recordset (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-4-server-returns-the-recordset-rds-tutorial.md)  
  
-   [Schritt 5: DataControl wird nutzbar gemacht (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)  
  
-   [Schritt 6: Änderungen werden an den Server (RDS-Tutorial) gesendet.](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)  
  
-   [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Schritt 1: Geben Sie eine Serverprogramm (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
