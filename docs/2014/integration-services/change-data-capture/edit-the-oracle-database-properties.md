---
title: Bearbeiten der Oracle-Datenbankeigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraProp
ms.assetid: 58dc99f1-ee6b-4508-bb66-2bc589611ff7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cfc119c031f0eeb84317cd1bcd8250f8ab803b6b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52770862"
---
# <a name="edit-the-oracle-database-properties"></a>Bearbeiten der Oracle-Datenbankeigenschaften
  Verwenden Sie die Registerkarte Oracle im Eigenschaften-Editor, um Änderungen an der Beschreibung vorzunehmen, die Sie im Assistenten für neue Instanzen auf der Seite Create CDC database angegeben haben, und um Änderungen an den Verbindungsinformationen zur Oracle Log Mining-Datenbank vorzunehmen.  
  
 Im Folgenden werden die Informationen auf der Registerkarte **Oracle** beschrieben.  
  
 **Name**  
 Der Name der CDC-Instanz, die Sie im Assistenten für neue Instanzen auf der Seite Create CDC Database eingegeben haben. Dieses Feld ist schreibgeschützt, und Sie können diese Informationen nicht bearbeiten.  
  
 **Beschreibung**  
 Sie können die Beschreibung der neuen Instanz bearbeiten oder eine Beschreibung hinzufügen, falls Sie diesen Schritt beim Erstellen der CDC-Instanz nicht ausgeführt haben.  
  
 **Oracle Connect String**  
 Dies ist die Oracle-Verbindungszeichenfolge zum Computer mit der verwendeten Oracle-Datenbank. Dieses Feld ist schreibgeschützt, und Sie können diese Informationen nicht bearbeiten. Dies liegt daran, dass bei bestimmten Änderungen an der Verbindungszeichenfolge für die Oracle CDC-Instanz möglicherweise auf eine völlig andere Oracle-Datenbank verwiesen wird, sodass der in der Tabelle **cdc.xdbcdc_config** gespeicherte CDC-Instanzstatus beschädigt wird. Wenn kleinere Änderungen erforderlich sind, können Sie die Verbindungszeichenfolge mithilfe von SQL Server Management Studio direkt in der Konfigurationstabelle ändern.  
  
 **Oracle Log Mining Authentication**  
 Um die Authentifizierungsinformationen für die Oracle-Datenbank einzugeben, in der die Log Mining-Komponente enthalten ist, wählen Sie unter **Authentifizierung**eine der folgenden Optionen aus:  
  
-   **Windows-Authentifizierung**: Wählen Sie diese Option, um die aktuellen Anmeldeinformationen für die Windows-Domäne verwenden. Sie können diese Option nur verwenden, wenn die Oracle-Datenbank für die Nutzung der Windows-Authentifizierung konfiguriert ist.  
  
-   **Oracle Authentication**: Wenn Sie diese Option auswählen, geben Sie die **Benutzernamen** und **Kennwort** für den Benutzer in der Sie eine Verbindung mit Oracle-Datenbank.  
  
 Sie können die Oracle-Datenbankeigenschaften im Viewer anzeigen. Beim Verwenden des Viewers sind die Informationen schreibgeschützt. Der Viewer enthält auch eine Liste der aufgezeichneten Spalten in der Tabelle. Informationen zum Zugriff auf den Viewer finden Sie unter [How to Manage a CDC Instance](manage-a-cdc-instance.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten eines CDC Service über die CDC Designer Console](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md)   
 [Herstellen einer Verbindung zu einer Oracle-Quelldatenbank](connect-to-an-oracle-source-database.md)   
 [Herstellen einer Verbindung mit Oracle](connect-to-oracle.md)  
  
  
