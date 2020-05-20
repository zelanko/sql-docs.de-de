---
title: OLE DB Anbieter (ADO) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a50ad68f7a4b40d008bd6d60b6d24e1984428e1
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759136"
---
# <a name="ole-db-providers-ado"></a>OLE DB-Anbieter (ADO)
OLE DB definiert einen Satz von COM-Schnittstellen, um Anwendungen einen einheitlichen Zugriff auf Daten bereitzustellen, die in verschiedenen Informationsquellen gespeichert sind. Dieser Ansatz ermöglicht es einer Datenquelle, die Daten über die Schnittstellen freizugeben, die die für die Datenquelle geeignete Menge an DBMS-Funktionalität unterstützen. Entwurfs bedingt basiert die Hochleistungs Architektur OLE DB auf der Verwendung eines flexiblen, komponentenbasierten Dienst Modells. Anstatt eine vorgeschriebene Anzahl von zwischengeschalteten Schichten zwischen der Anwendung und den Daten zu haben, erfordert OLE DB nur so viele Komponenten, wie zum Durchführen einer bestimmten Aufgabe benötigt werden.  
  
 Nehmen wir beispielsweise an, ein Benutzer möchte eine Abfrage ausführen. Betrachten Sie die folgenden Szenarien:  
  
-   Die Daten befinden sich in einer relationalen Datenbank, für die zurzeit ein ODBC-Treiber, aber kein System eigener OLE DB Anbieter vorhanden ist: die Anwendung verwendet ADO, um mit dem OLE DB Anbieter für ODBC zu kommunizieren, der dann den entsprechenden ODBC-Treiber lädt. Der Treiber übergibt die SQL-Anweisung an das DBMS, das die Daten abruft.  
  
-   Die Daten befinden sich in Microsoft SQL Server, für die ein System eigener OLE DB Anbieter vorhanden ist: die Anwendung verwendet ADO, um für Microsoft SQL Server direkt mit dem OLE DB Anbieter zu kommunizieren. Es sind keine Vermittler erforderlich.  
  
-   Die Daten befinden sich in Microsoft Exchange Server, für den es einen OLE DB Anbieter gibt, der jedoch keine Engine zum Verarbeiten von SQL-Abfragen verfügbar macht: die Anwendung verwendet ADO, um mit dem OLE DB Anbieter für Microsoft Exchange zu kommunizieren, und ruft eine OLE DB Abfrage Prozessor Komponente auf, um die Abfrage zu verarbeiten.  
  
-   Die Daten befinden sich im Microsoft NTFS-Dateisystem in Form von Dokumenten: auf Daten wird mithilfe eines systemeigenen OLE DB Anbieters über den Microsoft-Indizierungs Dienst zugegriffen, der den Inhalt und die Eigenschaften von Dokumenten im Dateisystem indiziert, um eine effiziente Inhalts Suche zu ermöglichen.  
  
 In allen vorherigen Beispielen kann die Anwendung die Daten Abfragen. Die Anforderungen des Benutzers werden mit einer minimalen Anzahl von Komponenten erfüllt. In jedem Fall werden zusätzliche Komponenten nur dann verwendet, wenn Sie benötigt werden und nur die erforderlichen Komponenten aufgerufen werden. Dieses Bedarfs gesteuerte Laden von wiederverwendbaren und Share baren Komponenten trägt bei der Verwendung OLE DB erheblich zu einer hohen Leistung bei.  
  
 Anbieter lassen sich in zwei Kategorien unterteilen: solche, die Daten bereitstellen Ein Datenanbieter besitzt seine eigenen Daten und macht Sie in tabellarischer Form für Ihre Anwendung verfügbar. Ein Dienstanbieter kapselt einen Dienst, indem er Daten erzeugt und nutzt, um Features in Ihren ADO-Anwendungen zu erweitern. Ein Dienstanbieter kann auch weiter als Dienst Komponente definiert werden, die in Verbindung mit anderen Dienstanbietern oder Komponenten funktionieren muss.  
  
 ADO bietet eine konsistente, übergeordnete Oberfläche für die verschiedenen OLE DB-Anbieter.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Datenanbieter](../../../ado/guide/data/data-providers.md)  
  
-   [Dienstanbieter und Komponenten](../../../ado/guide/data/service-providers-and-components.md)
