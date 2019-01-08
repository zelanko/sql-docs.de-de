---
title: Verteilereigenschaften (Verleger) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distproperties.publishers.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9ee329a923bf0b3c3c08b23fb6071a773dc16400
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52816442"
---
# <a name="distributor-properties-publishers"></a>Verteilereigenschaften (Verleger)
  Mithilfe der Seite **Verleger** des Dialogfelds **Verteilereigenschaften** können Sie es Verlegern ermöglichen, diesen Verteiler zu verwenden. Sie können auch zu diesen Verlegern gehörige Eigenschaften festlegen. Beachten Sie, dass dieser Server nicht zu einem Verleger wird, wenn Sie es einem Verleger ermöglichen, diesen Server als Verteiler zu verwenden. Sie müssen eine Verbindung mit dem Verleger herstellen, ihn für das Veröffentlichen konfigurieren und diesen Server als Verteiler auswählen. Sie können den Verleger konfigurieren und mithilfe des Assistenten für neue Veröffentlichung einen Verteiler auswählen.  
  
## <a name="options"></a>Optionen  
 **Verleger**  
 Wählen Sie die Server aus, die diesen Verteiler verwenden dürfen. Klicken Sie auf die Eigenschaftenschaltfläche (die Schaltfläche mit den **drei Punkten**) neben einem Verleger, um zusätzliche Eigenschaften anzuzeigen und festzulegen.  
  
 **Hinzufügen**  
 Wenn der von Ihnen gewünschte Server nicht in der Liste enthalten ist, klicken Sie auf **Hinzufügen** , um einen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger oder einen Oracle-Verleger zur Liste der verfügbaren Verleger hinzuzufügen. Wenn der von Ihnen hinzugefügte Server der erste Server ist, der diesen Verteiler als Remoteverteiler verwendet, werden Sie aufgefordert, ein Kennwort für administrative Verbindungen einzugeben.  
  
 **Kennwort für administrative Verbindung**  
 Verwenden Sie diese Option, um das Kennwort für die Verbindung zu aktualisieren, die die Replikation zwischen dem Verleger und dem Remoteverteiler mithilfe der **distributor_admin** -Anmeldung herstellt:  
  
-   Wenn der Verteiler nur als lokaler Verteiler dient, wird dieses Kennwort per Zufallsgenerator erstellt und automatisch konfiguriert.  
  
-   Wenn der Verteiler bereits einen Remoteverleger besitzt, wurde ein Kennwort bereits ursprünglich auf dieser Seite oder auf der Seite **Verteilerkennwort** des Verteilungskonfigurations-Assistenten angegeben.  
  
-   Wenn Sie den ersten Remoteverleger für diesen Verleger aktivieren, werden Sie aufgefordert, ein Kennwort einzugeben.  
  
 Weitere Informationen zur Sicherheit für Verteiler finden Sie unter [Schützen des Verteilers](security/secure-the-distributor.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Konfigurieren der Veröffentlichung und der Verteilung](configure-publishing-and-distribution.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](view-and-modify-distributor-and-publisher-properties.md)  
  
  
