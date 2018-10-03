---
title: Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 137f2f2e02e7e1dd91e93a246401108c68d00a11
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074400"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff
  In diesem Thema wird beschrieben, wie [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]Dateisystemzugriff auf den Ort gewährt wird, an dem die Datenbankdateien gespeichert sind. Der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Dienst muss vom Windows-Dateisystem die Berechtigung für den Zugriff auf den Dateiordner erhalten, in dem die Datenbankdateien gespeichert sind. Die Berechtigung für den Zugriff auf den Standardspeicherort wird bei der Ausführung von Setup konfiguriert. Wenn Sie Datenbankdateien an einem anderen Ort ablegen, müssen Sie u. U. die folgenden Schritte ausführen, um dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Vollzugriffsberechtigung auf diesen Ort zu gewähren.  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden der Pro-Dienst-SID Berechtigungen für alle enthaltenen Dienste zugewiesen. Dieses System unterstützt die Dienstisolierung und den gründlichen Schutz. Die Pro-Dienst-SID ergibt sich aus dem Dienstnamen und ist für jeden Dienst eindeutig. Im Thema [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](configure-windows-service-accounts-and-permissions.md) werden die Pro-Dienst-SID beschrieben und Namen im Abschnitt **Windows-Berechtigungen und Rechte**bereitgestellt. Der Pro-Dienst-SID muss die Zugriffsberechtigung für den Dateispeicherort zugewiesen werden.  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>So gewähren Sie der Pro-Dienst-SID eine Dateisystemberechtigung  
  
1.  Navigieren Sie im Windows-Explorer zu dem Speicherort im Dateisystem, an dem die Datenbankdateien gespeichert sind. Klicken Sie mit der rechten Maustaste auf den Dateisystemordner, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf der Registerkarte **Sicherheit** auf **Bearbeiten**und dann auf **Hinzufügen**.  
  
3.  Klicken Sie im Dialogfeld zum **Auswählen von Benutzern, Computer, Dienstkonto oder Gruppen** oben in der Speicherortliste auf **Speicherorte**, wählen Sie den Computernamen aus, und klicken Sie auf **OK**.  
  
4.  In der **Geben Sie die zu verwendenden Objektnamen** geben der Namen des pro-Dienst-SID, die in der Onlinedokumentation aufgeführt **konfigurieren Windows-Dienstkonten und-Berechtigungen**. (Für die [!INCLUDE[ssDE](../../includes/ssde-md.md)] pro-Dienst-SID verwendet **NT SERVICE\MSSQLSERVER** für eine Standardinstanz oder **NT SERVICE\MSSQL$ InstanceName** für eine benannte Instanz.)  
  
5.  Klicken Sie auf **Namen überprüfen** , um den Eintrag zu überprüfen. Bei der Überprüfung wird häufig der Fehler zurückgegeben, dass der Name nicht gefunden wurde. Wenn Sie auf **OK**klicken, wird das Dialogfeld **Mehrere Namen gefunden** angezeigt.  
  
6.  Wählen Sie jetzt entweder den pro-Dienst-SID, **MSSQLSERVER** oder **NT SERVICE\MSSQL$ InstanceName**, und klicken Sie dann auf **OK**.  
  
7.  Klicken Sie erneut auf **OK** , um zum Dialogfeld **Berechtigungen** zurückzukehren.  
  
8.  In der **Gruppen- oder Benutzernamen** Namen wählen die pro-Dienst-SID, und klicken Sie dann in der **Berechtigungen für** \<Name > Wählen Sie im der **zulassen** für dasKontrollkästchen **Vollzugriff**.  
  
9. Klicken Sie auf **Anwenden**und dann zweimal auf **OK** , um das Dialogfeld zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten der Datenbank-Engine-Dienste](manage-the-database-engine-services.md)   
 [Verschieben von Systemdatenbanken](../../relational-databases/databases/system-databases.md)   
 [Verschieben von Benutzerdatenbanken](../../relational-databases/databases/move-user-databases.md)  
  
  
