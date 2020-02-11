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
ms.openlocfilehash: 541c92cd34b9cbaecdd1001be29dbab8d9b194a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922414"
---
# <a name="rds-tutorial"></a>RDS-Tutorial
In diesem Tutorial wird veranschaulicht, wie Sie das RDS-Programmiermodell zum Abfragen und Aktualisieren einer Datenquelle verwenden. Zuerst werden die Schritte beschrieben, die zum Ausführen dieser Aufgabe erforderlich sind. Anschließend wird das Tutorial in Microsoft® Visual Basic Scripting Edition (mit ADO für Windows Foundation-Klassen (ADO/WFC)) wiederholt.  
  
 Dieses Tutorial ist aus zwei Gründen in verschiedenen Sprachen codiert:  
  
-   Die Dokumentation für RDS geht von den readercodes in Visual Basic aus. Dadurch ist die Dokumentation für Visual Basic Programmierer praktisch, aber für Programmierer, die andere Sprachen verwenden, weniger nützlich.  
  
-   Wenn Sie sich nicht sicher sind, was eine bestimmte RDS-Funktion ist und Sie eine andere Sprache kennen, können Sie Ihre Frage möglicherweise beheben, indem Sie nach derselben Funktion suchen, die in einer anderen Sprache ausgedrückt wird.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="how-the-tutorial-is-presented"></a>Präsentation des Tutorials  
 Dieses Tutorial basiert auf dem RDS-Programmiermodell. Dabei werden die einzelnen Schritte des Programmiermodells einzeln erläutert. Außerdem wird jeder Schritt mit einem Fragment Visual Basic Codes veranschaulicht.  
  
 Das Codebeispiel wird in anderen Sprachen mit minimaler Erörterung wiederholt. Jeder Schritt in einem bestimmten Lernprogramm für Programmiersprachen wird mit dem entsprechenden Schritt im Programmiermodell und im beschreibenden Tutorial gekennzeichnet. Verwenden Sie die Nummer des Schritts, um auf die Diskussion im beschreibenden Tutorial zu verweisen.  
  
 Das RDS-Programmiermodell wird im folgenden Abschnitt angegeben. Verwenden Sie es als Roadmap, während Sie das Tutorial durchgehen.  
  
## <a name="rds-programming-model-with-objects"></a>RDS-Programmiermodell mit Objekten  
  
-   Geben Sie das Programm an, das auf dem Server aufgerufen werden soll, und rufen Sie eine Methode (Proxy) ab, auf die vom Client aus verwiesen werden soll.  
  
-   Rufen Sie das Serverprogramm auf. Übergeben Sie Parameter an das Serverprogramm, das die Datenquelle und den auszugebenden Befehl identifiziert.  
  
-   Das Serverprogramm Ruft ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt aus der Datenquelle ab, in der Regel mithilfe von ADO. Optional wird das **Recordset** -Objekt auf dem Server verarbeitet.  
  
-   Das Serverprogramm gibt das endgültige **Recordset** -Objekt an die Client Anwendung zurück.  
  
-   Auf dem Client wird das **Recordset** -Objekt optional in ein Formular eingefügt, das von visuellen Steuerelementen problemlos verwendet werden kann.  
  
-   Änderungen am **Recordset** -Objekt werden zurück an den Server gesendet und zum Aktualisieren der Datenquelle verwendet.  
  
 Dieses Tutorial enthält die folgenden Themen.  
  
-   [Schritt 1: Serverprogramm angeben (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)  
  
-   [Schritt 2: Serverprogramm aufrufen (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)  
  
-   [Schritt 3: Server ruft ein Recordset ab (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)  
  
-   [Schritt 4: Server gibt das Recordset zurück (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-4-server-returns-the-recordset-rds-tutorial.md)  
  
-   [Schritt 5: DataControl wird nutzbar gemacht (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)  
  
-   [Schritt 6: Änderungen werden an den Server gesendet (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)  
  
-   [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schritt 1: Angeben eines Server Programms (RDS-Tutorial)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)   
 [RDS-Tutorial (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
