---
title: Statusleiste (Abfrage-Editor der Datenbank-Engine)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fe864d5f4f622237c5c7b92e5a1e717c26692ec
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243151"
---
# <a name="status-bar-database-engine-query-editor"></a>Statusleiste (Abfrage-Editor der Datenbank-Engine)
  Die Statusleiste des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fensters kann farblich codiert sein, um so anzuzeigen, mit welcher Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)] jedes Fenster verbunden ist.  
  
1.  Vorbereitungen **:**[Status leisten Farben](#StatusBarColors)    
  
2.  So **legen Sie eine Serverstatus Farbe in fest:**[Objekt-Explorer](#SetOEServerColor), [registrierter Server](#SetRegServerColor)    
  
3.  **Um eine Status Farbe zu verwenden:**  [Abfrage-Editor mithilfe einer Server Farbe öffnen](#OpenServerColor), [einen Abfrage-Editor mit einer Status Farbe öffnen](#OpenSpecColor)  
  
##  <a name="StatusBarColors"></a>Farben der Status Leiste  
 Sie können einem bestimmten Serverknoten in entweder **Objekt-Explorer** oder **Registrierte Server**eine Statusleistenfarbe zuordnen. Die Farben können nur für Serverknoten angegeben werden, die mit einer Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbunden sind, nicht aber für Serverknoten für andere SQL Server-Technologien. Ebenso können Sie eine benutzerdefinierte Statusleistenfarbe angeben, wann immer Sie ein neues [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fenster mit einer Instanz des [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbinden. Sie können dann entweder mit der für den Serverknoten definierten Statusfarbe ein Abfrage-Editor-Fenster öffnen oder eine eindeutige Farbe für dieses Editorfenster angeben.  
  
 Eine benutzerdefinierte Statusleistenfarbe für einen Serverknoten in Objekt-Explorer muss beim Herstellen der Verbindung festgelegt werden. Um die einem vorhandenen Serverknoten zugeordnete Farbe zu ändern, müssen Sie die Verbindung trennen und dann unter Angabe der neuen Farbe die Verbindung erneut herstellen.  
  
##  <a name="SetOEServerColor"></a>Festlegen der Status Farbe für einen Server in Objekt-Explorer  
 **So legen Sie eine Serverstatus Farbe in Objekt-Explorer**  
  
1.  Wählen Sie im **Objekt-Explorer** die Schaltfläche **Verbinden** und dann **Datenbank-Engine...** aus.  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** die Option **Optionen >>**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Benutzerdefinierte Farbe verwenden** .  
  
4.  Wählen Sie zur Festlegung der Farbe die Schaltfläche **Auswählen...** aus.  
  
5.  Wählen Sie entweder eine standardmäßige oder benutzerdefinierte Farbe aus und klicken Sie dann auf OK.  
  
6.  Geben Sie die restlichen Verbindungsinformationen ein und wählen Sie dann die Schaltfläche **Verbinden** aus.  
  
##  <a name="SetRegServerColor"></a>Festlegen der Status Farbe für einen registrierten Server  
 **So legen Sie eine Server Farbe für einen registrierten Server fest**  
  
1.  Klicken Sie unter **Registrierte Server** mit der rechten Maustaste auf einen Serverknoten, und wählen Sie dann **Eigenschaften...** aus.  
  
2.  Wählen Sie im Dialogfeld **Serverregistrierungseigenschaften bearbeiten** die Registerkarte **Verbindungseigenschaften** aus.  
  
3.  Aktivieren Sie das Kontrollkästchen **Benutzerdefinierte Farbe verwenden** .  
  
4.  Wählen Sie zur Festlegung der Farbe die Schaltfläche **Auswählen...** aus.  
  
5.  Wählen Sie entweder eine standardmäßige oder benutzerdefinierte Farbe aus und klicken Sie dann auf OK.  
  
6.  Wählen Sie im Dialogfeld **Serverregistrierungseigenschaften bearbeiten** die Schaltfläche **Speichern** aus.  
  
##  <a name="OpenServerColor"></a>Öffnen eines Editors mithilfe einer Server Farbe  
 **So öffnen Sie ein Editor Fenster mithilfe einer Server Farbe**  
  
-   Klicken Sie mit der rechten Maustaste entweder in **Objekt-Explorer** oder **Registrierte Server**auf einen Serverknoten, und wählen Sie **Neue Abfrage**aus.  
  
-   Markieren Sie alternativ einen Serverknoten und wählen Sie dann die Symbolleistenschaltfläche **Neue Abfrage** aus.  
  
-   Die Statusleiste im Editorfenster verwendet die für den zugeordneten Server definierte Farbe.  
  
##  <a name="OpenSpecColor"></a>Öffnen eines Editors unter Angabe einer Status Farbe  
 **So öffnen Sie ein Editor Fenster mit Angabe einer Status Farbe**  
  
-   Öffnen Sie das Menü **Datei**, wählen Sie **Neu** aus, und wählen Sie dann **Datenbank-Engine-Abfrage** aus.  
  
-   Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** die Option **Optionen >>**.  
  
-   Aktivieren Sie das Kontrollkästchen **Benutzerdefinierte Farbe verwenden** .  
  
-   Wählen Sie zur Festlegung der Farbe die Schaltfläche **Auswählen...** aus.  
  
-   Wählen Sie entweder eine standardmäßige oder benutzerdefinierte Farbe aus und klicken Sie dann auf OK.  
  
-   Geben Sie die restlichen Verbindungsinformationen ein und wählen Sie dann die Schaltfläche **Verbinden** aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfrage-und Text-Editoren &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
