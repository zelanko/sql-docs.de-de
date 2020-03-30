---
title: 'Schritt 3: Hinzufügen und Konfigurieren eines OLE DB-Verbindungs-Managers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4bf9a4a922c8aeed7ca344b423193e8b01c19037
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71296143"
---
# <a name="lesson-1-3-add-and-configure-an-ole-db-connection-manager"></a>Lektion 1.3: Hinzufügen und Konfigurieren eines OLE DB-Verbindungs-Managers

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Nach dem Hinzufügen eines Verbindungs-Managers für Flatfiles zum Herstellen einer Verbindung mit der Datenquelle müssen Sie den OLE DB-Verbindungs-Manager zum Herstellen einer Verbindung mit dem Ziel hinzufügen. Ein OLE DB-Verbindungs-Manager ermöglicht einem Paket das Extrahieren von Daten aus einer oder das Laden von Daten in eine OLE DB-kompatible(n) Datenquelle. Mithilfe einer OLE DB-Verbindungs-Manager-Instanz können Sie den Server, die Authentifizierungsmethode und die Standarddatenbank für die Verbindung angeben.  
  
In dieser Aufgabe erstellen Sie eine OLE DB-Verbindungs-Manager-Instanz, die die Windows-Authentifizierung zum Herstellen einer Verbindung mit der lokalen Instanz von **AdventureWorksDW2012** verwendet. Auf die von Ihnen erstellte OLE DB-Verbindungs-Manager-Instanz wird auch von anderen Komponenten verwiesen, die Sie später in diesem Tutorial erstellen werden. Dazu gehören die Lookup-Transformation und das OLE DB-Ziel.  
  
## <a name="add-and-configure-an-ole-db-connection-manager"></a>Hinzufügen und Konfigurieren eines OLE DB-Verbindungs-Managers

1. Klicken Sie im Bereich **Projektmappen-Explorer** mit der rechten Maustaste auf **Verbindungs-Manager**, und wählen Sie **Neuer Verbindungs-Manager** aus.

1. Klicken Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** erst auf die Option **OLEDB** und dann auf **Hinzufügen**.
    
2. Klicken Sie im Dialogfeld **OLE DB-Verbindungs-Manager konfigurieren** auf **Neu**.  
  
3. Geben Sie für **Servername**den Namen **localhost**ein.  
  
    Wenn Sie localhost als Servernamen angeben, stellt der Verbindungs-Manager eine Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf dem lokalen Computer her. Wenn Sie eine Remoteinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verwenden möchten, ersetzen Sie localhost durch den Namen des Servers, mit dem Sie eine Verbindung herstellen möchten.  
  
4. Überprüfen Sie in der Gruppe **Am Server anmelden** , ob **Windows-Authentifizierung verwenden** ausgewählt ist.  
  
5. Geben Sie in der Gruppe **Mit Datenbank verbinden** im Feld **Datenbanknamen eingeben oder auswählen** den Wert **AdventureWorksDW2012**ein, oder wählen Sie ihn aus.  
  
6. Klicken Sie auf **Verbindung testen**, um zu überprüfen, ob die von Ihnen angegebenen Verbindungseinstellungen gültig sind.  
  
7. Klicken Sie auf **OK**.  
  
8. Klicken Sie auf **OK**.  
  
9. Überprüfen Sie im Bereich **Verbindungs-Manager**, ob die Option **localhost.AdventureWorksDW2012** ausgewählt ist.  
  

## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 4: Hinzufügen eines Datenflusstasks zum Paket](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Teilcache](../integration-services/connection-manager/ole-db-connection-manager.md)  
  
