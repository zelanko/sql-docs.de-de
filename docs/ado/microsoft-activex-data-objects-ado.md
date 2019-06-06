---
title: Microsoft ActiveX Data Objects (ADO) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, about
ms.assetid: 2fa6237b-44b8-4b6c-9952-5acd80a54e20
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 05cc5d08785b116f4e4dd27b8a0a61b34a14d473
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66699399"
---
# <a name="microsoft-activex-data-objects-ado"></a>Microsoft ActiveX-Datenobjekte (ADO)

ADO wird in C++-Programmen verwendet, um die Verbindung mit SQL Server. Natürlich funktioniert es auch zur Verbindung mit Azure SQL-Datenbank in der Cloud.

Jeder Abschnitt in diesem Artikel wird beschrieben, eine Komponente von ADO.

> [!NOTE]
> ADO.NET ist anders als ADO. ADO.NET und viele andere SQL-Verbindung-Treiber und den Sprachen, werden beginnend mit erläutert [SQL Server-Treiber](../connect/sql-connection-libraries.md).

  
## <a name="ado"></a>ADO  
 Microsoft ActiveX Data Objects (ADO) aktivieren Sie Ihre Clientanwendungen aufrufen und Bearbeiten von Daten aus einer Vielzahl von Quellen, die über einen OLE DB-Anbieter. Die primären Vorteile sind einfache Verwendung, hohe Geschwindigkeit, geringer Arbeitsspeicher- und Speicherplatzbedarf. ADO unterstützt wichtige Features zum Erstellen von Client/Server- und webbasierten Anwendungen.  
  
## <a name="ado-md"></a>ADO MD  
 Microsoft ActiveX Data Objects (Multidimensional) (ADO MD) bietet einfachen Zugriff auf mehrdimensionale Daten aus den Sprachen wie Microsoft Visual Basic und Microsoft Visual C++. ADO MD erweitert Microsoft ActiveX Data Objects (ADO) Objekte für mehrdimensionale Daten, z. B. die CubeDef und Cellset-Objekte. Mit ADO MD können Sie mehrdimensionales Schema durchsuchen, Abfragen ein Cubes und die Ergebnisse abzurufen.  
  
 ADO MD verwendet wie ADO zugrunde liegenden OLE DB-Anbieter für den Zugriff auf Daten. Zum Arbeiten mit ADO MD muss der Anbieter einen Anbieter für mehrdimensionale Daten (MDP) sein, wie in der OLE DB für OLAP-Spezifikation definiert. MDPs Daten in multidimensionalen Sichten im Gegensatz zu tabellarischen Datenanbieter (TDPs) diese Darstellung der Daten in tabellarische Sichten. Lesen Sie die Dokumentation für den OLAP-OLE DB-Anbieter für ausführlichere Informationen zur spezifischen Syntax und Verhalten, die von Ihrem Anbieter unterstützt.  
  
## <a name="rds"></a>RDS  
 Remote Data Service (RDS) ist ein Feature von ADO mit dem Verschieben von Daten von einem Server in einer Clientanwendung oder der Webseite, bearbeiten die Daten auf dem Client und Updates in einem einzelnen Roundtrip an den Server zurückgeben.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="adox"></a>ADOX  
 Microsoft ActiveX Data Objects-Extensions für Datendefinitionssprache und Sicherheit (ADOX) ist eine Erweiterung der ADO-Objekte und -Programmiermodell verwendet. ADOX enthält Objekte für die Schema-Erstellung und Änderung sowie Sicherheit. Da es sich um eine schemabearbeitung Vorgehensweise objektbasiert ist, können Sie Code schreiben, die für verschiedene Datenquellen unabhängig von deren systemeigenen Syntax verwendet werden.  
  
 ADOX ist eine zugehörige Bibliothek mit den Kernobjekten für ADO. Er macht zusätzliche Objekte zum Erstellen, ändern und Löschen von Schemaobjekten, z. B. Tabellen und Prozeduren verfügbar. Darüber hinaus wird die Sicherheitsobjekte, um Benutzer und Gruppen verwalten und zu erteilen und Widerrufen von Berechtigungen für Objekte enthält.  
  
## <a name="documentation"></a>Dokumentation  
 [ADO Security Design Issues (Entwurfsaspekte für die ADO-Sicherheit)](../ado/guide/ado-security-design-issues.md)  
  
 [ADO Programmer's Guide (Programmierhandbuch zu ADO)](../ado/guide/ado-programmer-s-guide.md)  
  
 Eine Einführung in das Verwenden von ADO, RDS, ADO MD und ADOX.  
  
 [ADO-Programmierreferenz](../ado/reference/ado-programmer-s-reference.md)  
  
 Dieser Abschnitt der ADO-Dokumentation enthält Themen für ADO, RDS, ADO MD und ADOX-Objekt, Sammlung, Eigenschaft, dynamische Eigenschaft, Methode, Ereignis, und -Enumeration.  
  
 [ADO-Glossar](../ado/ado-glossary.md)  
  
## <a name="support"></a>Support  
 Kostenlos mit ADO-Problemen helfen, versuchen Sie es bereitstellen für die öffentliche ADO-Newsgroup. Von Supportmitarbeitern von Microsoft Product Support Services (PSS), die ADO behandelt und von anderen erfahrenen Entwicklern von ADO, wird dieser Newsgroup an, überwacht.  
  
 Weitere Informationen zu Supportoptionen finden Sie auf der Website Microsoft Help und unterstützen.


