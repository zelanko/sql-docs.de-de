---
description: Microsoft ActiveX-Datenobjekte (ADO)
title: Microsoft ActiveX Data Objects (ADO) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.topic: conceptual
helpviewer_keywords:
- ADO, about
ms.assetid: 2fa6237b-44b8-4b6c-9952-5acd80a54e20
author: rothja
ms.author: jroth
ms.openlocfilehash: a63b254397e45fdba56f3d86cdcf45069f9265fb
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91721241"
---
# <a name="microsoft-activex-data-objects-ado"></a>Microsoft ActiveX-Datenobjekte (ADO)

ActiveX Data Objects ist ein Programmiermodell, was bedeutet, dass es nicht von einem beliebigen Back-End-Modul abhängt. Derzeit ist die einzige Engine, die das ADO-Modell unterstützt, jedoch OLE-DB. Es gibt zahlreiche Native OLE DB-Anbieter und einen OLE DB-Anbieter für ODBC. ADO wird in C++-und Visual Basic Programmen verwendet, um eine Verbindung mit SQL Server und anderen Datenbanken herzustellen. Natürlich funktioniert es auch, um eine Verbindung mit Azure SQL-Datenbank in der Cloud herzustellen.

In jedem Abschnitt dieses Artikels wird eine Komponente von ADO beschrieben.

> [!NOTE]
> ADO.NET unterscheidet sich von ADO. ADO.net und viele andere SQL-Verbindungs Treiber und deren Sprachen werden ab [SQL Server Treibern](../connect/sql-connection-libraries.md)erläutert.

  
## <a name="ado"></a>ADO  
 Microsoft ActiveX Data Objects (ADO) ermöglicht Ihren Client Anwendungen den Zugriff auf und die Bearbeitung von Daten aus einer Vielzahl von Quellen über einen OLE DB-Anbieter. Zu den Hauptvorteilen gehören Benutzerfreundlichkeit, hohe Geschwindigkeit, wenig Arbeitsspeicher und wenig Speicherbedarf. ADO unterstützt wichtige Features zum Entwickeln von Client-/Server-und webbasierten Anwendungen.  
  
## <a name="ado-md"></a>ADO MD  
 Microsoft ActiveX Data Objects (Multidimensional) (ADO MD) bietet einfachen Zugriff auf mehrdimensionale Daten aus Sprachen wie Microsoft Visual Basic und Microsoft Visual C++. ADO MD erweitert Microsoft ActiveX Data Objects (ADO) um Objekte, die für mehrdimensionale Daten, z. b. die CubeDef-und Cellset-Objekte, spezifisch sind. Mit ADO MD Sie das mehrdimensionale Schema durchsuchen, einen Cube Abfragen und die Ergebnisse abrufen können.  
  
 Wie ADO verwendet ADO MD einen zugrunde liegenden OLE DB-Anbieter, um Zugriff auf Daten zu erhalten. Um mit ADO MD arbeiten zu können, muss der Anbieter ein mehrdimensionaler Datenanbieter (MDP) sein, wie in der OLE DB für OLAP-Spezifikation definiert. MDPs stellen Daten in mehrdimensionalen Ansichten im Gegensatz zu tabellarischen Datenanbietern (TDPs) dar, die Daten in Tabellen Sichten darstellen. Ausführlichere Informationen zur spezifischen Syntax und den von Ihrem Anbieter unterstützten Verhalten finden Sie in der Dokumentation für Ihren OLAP-OLE DB-Anbieter.  
  
## <a name="rds"></a>RDS  
 Remote Data Service (RDS) ist ein Feature von ADO, mit dem Sie Daten von einem Server auf eine Client Anwendung oder Webseite verschieben, die Daten auf dem Client bearbeiten und in einem einzelnen Roundtrip Updates an den Server zurückgeben können.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu  [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="adox"></a>ADOX  
 Microsoft ActiveX Data Objects Extensions für Data Definition Language und Security (ADOX) ist eine Erweiterung der ADO-Objekte und des Programmiermodells. ADOX umfasst Objekte für das Erstellen und Ändern von Schemas sowie für die Sicherheit. Da es sich um einen objektbasierten Ansatz für die Schema Bearbeitung handelt, können Sie Code schreiben, der unabhängig von den Unterschieden in der nativen Syntax für verschiedene Datenquellen verwendet werden kann.  
  
 ADOX ist eine begleitende Bibliothek zu den Kern-ADO-Objekten. Es macht zusätzliche Objekte zum Erstellen, ändern und Löschen von Schema Objekten verfügbar, z. b. Tabellen und Prozeduren. Außerdem enthält es Sicherheits Objekte zum Verwalten von Benutzern und Gruppen sowie zum erteilen und widerrufen von Berechtigungen für Objekte.  
  
## <a name="documentation"></a>Dokumentation  
 [Entwurfsaspekte für die ADO-Sicherheit](./guide/ado-security-design-issues.md)  
  
 [ADO-Programmierhandbuch](./guide/ado-programmer-s-guide.md)  
  
 Eine Einführung in die Verwendung von ADO, RDS, ADO MD und ADOX.  
  
 [ADO-Programmierreferenz](./reference/ado-programmer-s-reference.md)  
  
 Dieser Abschnitt der ADO-Dokumentation enthält Themen für jedes ADO-, RDS-, ADO MD-und ADOX-Objekt, jede Auflistung, jede Eigenschaft, jede dynamische Eigenschaft, jede Methode, jedes Ereignis und jede Enumeration.  
  
 [ADO-Glossar](./ado-glossary.md)  
  
## <a name="support"></a>Support  
 Um kostenlose Hilfe bei ADO-Problemen zu erhalten, versuchen Sie, die Veröffentlichung an die öffentliche "ADO-News Diese Newsgroup wird von den Supportmitarbeitern von Microsoft-Produktsupport Services (PSS) überwacht, die ADO und andere erfahrene ADO-Entwickler abdecken.  
  
 Weitere Informationen zu Supportoptionen finden Sie auf der Microsoft Hilfe-und Support-Website.