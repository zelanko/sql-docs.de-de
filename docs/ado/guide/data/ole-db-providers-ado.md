---
title: OLE DB-Anbieter (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 6e0488c3-934d-4976-99dc-65c580dc7a3c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b3f4f1d4efed51a8f9e3b5eaf3bd4a2c7f385e75
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63034991"
---
# <a name="ole-db-providers-ado"></a>OLE DB-Anbieter (ADO)
OLE DB definiert einen Satz von COM-Schnittstellen für Anwendungen mit einheitlichen Zugriff auf Daten bereitzustellen, die in verschiedenen Datenquellen gespeichert sind. Dieser Ansatz ermöglicht eine Datenquelle, die Daten über die Schnittstellen freizugeben, die Menge der DBMS-Funktionen, die für die Datenquelle zu unterstützen. Standardmäßig basiert die Hochleistungs-Architektur von OLE DB für die Verwendung eines flexiblen, komponentenbasierte Services-Modells. Anstatt einer vorgegebenen Anzahl von zwischengeschalteten Schichten zwischen der Anwendung und die Daten, erfordert die OLE DB nur, wie viele Komponenten, wie die an eine bestimmte Aufgabe auszuführen.  
  
 Nehmen wir beispielsweise an, dass ein Benutzer eine Abfrage ausführen möchte. Betrachten Sie die folgenden Szenarien:  
  
-   Die Daten befinden sich in einer relationalen Datenbank, die für die es zurzeit vorhanden ein ODBC-Treiber, aber keine native OLE DB-Anbieter ist: Die Anwendung verwendet ADO, um die Kommunikation mit dem OLE DB-Anbieter für ODBC, klicken Sie dann den entsprechenden ODBC-Treiber lädt. Der Treiber übergibt SQL-Anweisung für das DBMS an, das die Daten abruft.  
  
-   Die Daten befinden sich in Microsoft SQL Server für die ein native OLE DB-Anbieter vorhanden ist: Die Anwendung verwendet ADO, um direkt mit der OLE DB-Anbieter für Microsoft SQL Server zu kommunizieren. Es sind keine Zwischenkomponenten erforderlich.  
  
-   Die Daten befinden sich in Microsoft Exchange Server, für die OLE DB-Anbieter vorhanden ist, aber die nicht auf ein Modul zum Verarbeiten von SQL-Abfragen verfügbar macht: Die Anwendung verwendet ADO, um die Kommunikation mit dem OLE DB-Anbieter für Microsoft Exchange und ruft bei einem OLE DB-abfrageverarbeitungskomponente zum Verarbeiten der Abfragen.  
  
-   Die Daten, die in der Microsoft-NTFS-Dateisystem in Form von Dokumenten gespeichert werden: Daten erfolgt über einen systemeigenen OLE DB-Anbieter für Microsoft Indexdienst, der den Inhalt und Eigenschaften von Dokumenten, in das Dateisystem indiziert, um effiziente Suchvorgänge für Inhalt zu aktivieren.  
  
 In den vorherigen Beispielen kann die Anwendung die Daten Abfragen. Die Anforderungen des Benutzers, die mit einer minimalen Anzahl von Komponenten erfüllt sind. In jedem Fall zusätzliche Komponenten werden verwendet, nur im Bedarfsfall, und nur die erforderlichen Komponenten werden aufgerufen. Diese bedarfsgesteuertes Laden von wiederverwendbaren und freigegebenen Komponenten trägt erheblich auf eine hohe Leistung, wenn die OLE DB verwendet wird.  
  
 Anbieter können in zwei Kategorien unterteilt: die Bereitstellung von Daten und die Dienste bereitstellen. Ein Datenanbieter besitzt seine eigenen Daten und macht Sie es in tabellarischer Form für Ihre Anwendung verfügbar. Ein Dienstanbieter kapselt einen Dienst durch erzeugen und Nutzen von Daten, Erweitern von Funktionen in den ADO-Anwendungen verwendet wird. Ein Dienstanbieter kann auch weiter als eine Dienstkomponente definiert werden die in Verbindung mit anderen Dienstanbietern oder Komponenten funktionieren müssen.  
  
 ADO bietet eine konsistente Schnittstelle auf die verschiedenen OLE DB-Anbieter hoher Ebene.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Datenanbieter](../../../ado/guide/data/data-providers.md)  
  
-   [Dienstanbieter und Komponenten](../../../ado/guide/data/service-providers-and-components.md)
