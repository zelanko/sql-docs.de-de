---
title: Konfiguration des Datenbankmoduls - Benutzerinstanz | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- database engine configuration
- database engine configuration, user instance
ms.assetid: dfc27c1e-0fe2-4221-bed5-f52667ddd3c8
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 00ce0b457fcb64c8568662ce4a64b8929c29e5ff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058012"
---
# <a name="database-engine-configuration---user-instance"></a>Konfiguration der Datenbank-Engine - Benutzerinstanz
  Mithilfe der Seite **Benutzerinstanz** können Sie eine separate Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] für Benutzer ohne Administratorberechtigungen generieren. Zudem können Sie der Administratorrolle Benutzer hinzufügen.  
  
## <a name="option"></a>Option  
 Benutzerinstanzen aktivieren  
 Standardmäßig aktiviert. Um die Funktionalität zum Aktivieren von Benutzerinstanzen zu deaktivieren, deaktivieren Sie das Kontrollkästchen.  
  
 Die Benutzerinstanz, auch bekannt als untergeordnete Instanz oder Clientinstanz, ist eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die durch die übergeordnete Instanz (die primäre Instanz, die wie [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]als Dienst ausgeführt wird) für den Benutzer generiert wurde. Die Benutzerinstanz wird als Benutzerprozess in dem Sicherheitskontext des Benutzers ausgeführt. Die Benutzerinstanz ist von der übergeordneten Instanz und anderen Benutzerinstanzen, die auf dem Computer ausgeführt werden, isoliert. Im Zusammenhang mit der Benutzerinstanzfunktion wird auch der Ausdruck "Ausführen von Instanzen als normaler Benutzer" (RANU, Run As Normal User) verwendet.  
  
> [!NOTE]  
>  Während des Setups als Mitglieder der festen Serverrolle **sysadmin** bereitgestellte Anmeldungen werden in der Vorlagendatenbank als Administratoren bereitgestellt. Sie sind so lange Mitglieder der festen Serverrolle **sysadmin** auf der Benutzerinstanz, bis sie entfernt werden.  
  
 Benutzer zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administratorrolle hinzufügen  
 Standardmäßig deaktiviert. Aktivieren Sie dieses Kontrollkästchen, um den aktuellen Setupbenutzer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administratorrolle hinzuzufügen.  
  
 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]-Benutzer, die Mitglieder von VORDEFINIERT\Administratoren sind, werden nicht automatisch der festen Serverrolle sysadmin hinzugefügt, wenn sie eine Verbindung mit [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] herstellen. Nur [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] -Benutzer, die explizit einer Administratorrolle auf Serverebene hinzugefügt wurden, können [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]verwalten. Mitglieder der Gruppe VORDEFINIERT\Administratoren können eine Verbindung mit der [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] -Instanz herstellen, verfügen jedoch nur über begrenzte Berechtigungen für Datenbankaufgaben. Daher müssen Benutzern, deren [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] -Berechtigungen in früheren Versionen von Windows von VORDEFINIERT\Administratoren und VORDEFINIERT\Benutzer vererbt wurden, unter [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] explizit Administratorberechtigungen in Instanzen von [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)]erteilt werden.  
  
 Wenn Sie nach Beendigung dieses Installationsprogramms Änderungen an Benutzerrollen vornehmen möchten, verwenden Sie das Oberflächen-Konfigurationstool von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (SQLSAC.exe). Klicken Sie zum Aktualisieren der Liste der Benutzer in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemadministratorrolle auf den Link **Neuen Administrator hinzufügen** .  
  
 Stellen Sie sicher, dass im Feld **Bereitstellung für Benutzer** die Angaben zu Domänenname\Benutzername des Benutzers aufgeführt sind, dessen Berechtigungen aktualisiert werden sollen. Wählen Sie aus der Liste der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen im Bereich **Verfügbare Privilegien** die zu aktualisierende Rolle aus, und klicken Sie dann auf den Pfeil nach rechts. Wenn Sie den Benutzer allen verfügbaren Rollen für alle verfügbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen und allen verfügbaren Rollen hinzufügen möchten, klicken Sie auf den doppelten Pfeil nach rechts.  
  
 Klicken Sie zum Implementieren der Änderungen nach Abschluss der Auswahl auf [!INCLUDE[clickOK](../../includes/clickok-md.md)]. Klicken Sie auf **Abbrechen**, wenn Sie das Tool beenden möchten, ohne Änderungen vorzunehmen.  
  
  