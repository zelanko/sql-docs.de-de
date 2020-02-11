---
title: 'Schritt 3: Hinzufügen und Konfigurieren eines OLE DB-Verbindungs-Managers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c22c9ca183a5975b762fd166ee434f305422e6ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62891719"
---
# <a name="step-3-adding-and-configuring-an-ole-db-connection-manager"></a>Schritt 3: Hinzufügen und Konfigurieren eines OLE DB-Verbindungs-Managers
  Nach dem Hinzufügen eines Flatfile-Verbindungs-Managers zum Herstellen einer Verbindung mit der Datenquelle besteht die nächste Aufgabe im Hinzufügen eines OLE DB-Verbindungs-Managers zum Herstellen einer Verbindung mit dem Ziel. Ein OLE DB-Verbindungs-Manager ermöglicht einem Paket das Extrahieren von Daten aus einer oder das Laden von Daten in eine OLE DB-kompatible(n) Datenquelle. Mithilfe des OLE DB-Verbindungs-Managers können Sie den Server, die Authentifizierungsmethode und die Standarddatenbank für die Verbindung angeben.  
  
 In dieser Lektion erstellen Sie einen OLE DB-Verbindungs-Manager, der die Windows-Authentifizierung zum Herstellen einer Verbindung mit der lokalen Instanz von **AdventureWorksDB2012**verwendet. Der von Ihnen erstellte OLE DB-Verbindungs-Manager wird auch von anderen Komponenten referenziert, die Sie später in diesem Lernprogramm erstellen werden. Dazu gehören die Transformation zum Suchen und das OLE DB-Ziel.  
  
### <a name="to-add-and-configure-an-ole-db-connection-manager-to-the-ssis-package"></a>So fügen Sie dem SSIS-Paket einen OLE DB-Verbindungs-Manager hinzu und konfigurieren ihn  
  
1.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im **Verbindungs-Manager** -Bereich und anschließend auf **Neue OLE DB-Verbindung**.  
  
2.  Klicken Sie im Dialogfeld **OLE DB-Verbindungs-Manager konfigurieren** auf **Neu**.  
  
3.  Geben Sie für **Servername**den Namen **localhost**ein.  
  
     Wenn Sie localhost als Servernamen angeben, stellt der Verbindungs-Manager eine Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf dem lokalen Computer her. Wenn Sie eine Remoteinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verwenden möchten, ersetzen Sie localhost durch den Namen des Servers, mit dem Sie eine Verbindung herstellen möchten.  
  
4.  Überprüfen Sie in der Gruppe **Am Server anmelden** , ob **Windows-Authentifizierung verwenden** ausgewählt ist.  
  
5.  Geben Sie in der Gruppe **Verbindung mit einer Datenbank herstellen** im Feld **Datenbanknamen eingeben oder** auswählen den Text ein `AdventureWorksDW2012`, oder wählen Sie ihn aus.  
  
6.  Klicken Sie auf **Verbindung testen** , um zu überprüfen, ob die von Ihnen angegebenen Verbindungseinstellungen gültig sind.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie auf **OK**.  
  
9. Überprüfen Sie im Dialogfeld **OLE DB-Verbindungs-Manager konfigurieren** im Bereich **Datenverbindungen** , ob **localhost.AdventureWorksDW2012** ausgewählt ist.  
  
10. Klicken Sie auf **OK**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Schritt 4: Hinzufügen eines Datenflusstasks zum Paket](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md)  
  
  
