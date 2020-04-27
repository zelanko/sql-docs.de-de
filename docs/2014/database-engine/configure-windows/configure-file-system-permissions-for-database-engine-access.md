---
title: Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b23ed3a3a1f128d24bfec2a0066e63b09753311a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62811324"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff
  In diesem Thema wird beschrieben, wie [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]Dateisystemzugriff auf den Ort gewährt wird, an dem die Datenbankdateien gespeichert sind. Der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Dienst muss vom Windows-Dateisystem die Berechtigung für den Zugriff auf den Dateiordner erhalten, in dem die Datenbankdateien gespeichert sind. Die Berechtigung für den Zugriff auf den Standardspeicherort wird bei der Ausführung von Setup konfiguriert. Wenn Sie Datenbankdateien an einem anderen Ort ablegen, müssen Sie u. U. die folgenden Schritte ausführen, um dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Vollzugriffsberechtigung auf diesen Ort zu gewähren.  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden der Pro-Dienst-SID Berechtigungen für alle enthaltenen Dienste zugewiesen. Dieses System unterstützt die Dienstisolierung und den gründlichen Schutz. Die Pro-Dienst-SID ergibt sich aus dem Dienstnamen und ist für jeden Dienst eindeutig. Im Thema [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](configure-windows-service-accounts-and-permissions.md) werden die Pro-Dienst-SID beschrieben und Namen im Abschnitt **Windows-Berechtigungen und Rechte**bereitgestellt. Der Pro-Dienst-SID muss die Zugriffsberechtigung für den Dateispeicherort zugewiesen werden.  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>So gewähren Sie der Pro-Dienst-SID eine Dateisystemberechtigung  
  
1.  Navigieren Sie im Windows-Explorer zu dem Speicherort im Dateisystem, an dem die Datenbankdateien gespeichert sind. Klicken Sie mit der rechten Maustaste auf den Dateisystemordner, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf der Registerkarte **Sicherheit** auf **Bearbeiten**und dann auf **Hinzufügen**.  
  
3.  Klicken Sie im Dialogfeld zum **Auswählen von Benutzern, Computer, Dienstkonto oder Gruppen** oben in der Speicherortliste auf **Speicherorte**, wählen Sie den Computernamen aus, und klicken Sie auf **OK**.  
  
4.  Geben Sie im Feld **Geben Sie die zu ausgewäfenden Objektnamen** ein den Namen der pro-Dienst-SID ein, die im Thema **Konfigurieren von Windows-Dienst Konten und-Berechtigungen**aufgeführt ist. (Verwenden Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] für die pro-Dienst-SID **NT service\mssqlserver** für eine Standard Instanz oder **NT service\mssql $ instanceName** für eine benannte Instanz.)  
  
5.  Klicken Sie auf **Namen überprüfen** , um den Eintrag zu überprüfen. Bei der Überprüfung wird häufig der Fehler zurückgegeben, dass der Name nicht gefunden wurde. Wenn Sie auf **OK**klicken, wird das Dialogfeld **Mehrere Namen gefunden** angezeigt.  
  
6.  Wählen Sie nun die pro-Dienst-SID aus, entweder **MSSQLSERVER** oder **NT service\mssql $ instanceName**, und klicken Sie dann auf **OK**.  
  
7.  Klicken Sie erneut auf **OK** , um zum Dialogfeld **Berechtigungen** zurückzukehren.  
  
8.  Wählen Sie im Feld **Gruppen-oder Benutzer** Namen die pro-Dienst-SID aus, und aktivieren Sie dann im Feld **Berechtigungen für** \<Name> das Kontrollkästchen **zulassen** für **voll**Zugriff.  
  
9. Klicken Sie auf **Anwenden**und dann zweimal auf **OK** , um das Dialogfeld zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten der Datenbank-Engine-Dienste](manage-the-database-engine-services.md)   
 [Verschieben von Systemdatenbanken](../../relational-databases/databases/system-databases.md)   
 [Verschieben von Benutzerdatenbanken](../../relational-databases/databases/move-user-databases.md)  
  
  
