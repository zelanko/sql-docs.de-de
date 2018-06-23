---
title: Erstellen eines Modells mithilfe des Berichts-Manager | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- report models [Reporting Services], creating
- Report Manager [Reporting Services], model creation
ms.assetid: 8e5d2bd3-48ec-45f3-afee-6d86797c8f28
caps.latest.revision: 28
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 9f4de8368cadbc56819cd22c65892cbf143ae02c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048470"
---
# <a name="create-a-model-using-report-manager"></a>Erstellen eines Modells mithilfe des Berichts-Managers
  Mithilfe des Berichts-Managers können Sie Modelle auf der Grundlage eines [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Cubes, einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank oder einer Oracle-Datenbank generieren. Berichtsmodelle werden aus freigegebenen Datenquellen generiert, die auf dem Berichtsserver veröffentlicht werden. Wenn Sie noch nicht über eine freigegebene Datenquelle verfügen, müssen Sie sie erstellen.  
  
 Das von Ihnen generierte Berichtsmodell basiert vollständig auf dem Schema der freigegebenen Datenquelle. Sie können weder auswählen, welche Teile der Datenquelle im Modell enthalten sind, noch können Sie die Regeln oder Metadaten eines generierten Modells bearbeiten. Sie können jedoch Eigenschaften für das Modell festlegen, nachdem es generiert wurde, und Rollenzuweisungen definieren, die den Zugriff auf das gesamte Modell oder auf Teile desselben einschränken.  
  
> [!NOTE]  
>  Ein Oracle-basiertes Modell generiert, mit dem Berichts-Manager oder [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 [!INCLUDE[SPS2010](../includes/sps2010-md.md)] enthält Datenbankobjekte, die einen Teil des Schemas für das Benutzerkonto für die Verbindung mit der Oracle-Datenquelle verwendet werden. Der Name des Benutzerkontos wird in den Anmeldeinformationen für die Datenquelleneigenschaften angegeben.  
  
### <a name="to-create-a-new-data-source-for-a-report-model-using-report-manager"></a>So erstellen Sie mithilfe des Berichts-Managers eine neue Datenquelle für ein Berichtsmodell  
  
1.  Geben Sie in der Adressleiste des Webbrowsers die URL für den Berichtsserver ein.  
  
2.  Klicken Sie auf **Neue Datenquelle**.  
  
3.  Geben Sie im Feld **Name** einen Namen für die Datenquelle ein.  
  
4.  Geben Sie optional eine kurze Beschreibung in das Textfeld **Beschreibung** ein.  
  
5.  Überprüfen Sie, ob das Kontrollkästchen **Diese Datenquelle aktivieren** aktiviert ist.  
  
6.  Wählen Sie in der Liste **Verbindungstyp** den Typ der Datenquelle aus, mit der Sie eine Verbindung herstellen möchten. Als Verbindungstyp muss einer der folgenden angegeben werden: **Oracle**, **Microsoft SQL Server** oder **Microsoft SQL Server Analysis Services**.  
  
7.  Geben Sie im Feld **Verbindungszeichenfolge** die Verbindungszeichenfolge ein, die auf die Datenbank zeigt.  
  
8.  Wählen Sie die Verbindungsmethode aus, die Benutzer des Berichts-Generators zum Herstellen der Verbindung mit der Datenbank verwenden müssen.  
  
    -   Windows-Authentifizierung: Wählen Sie diese Option aus, wenn [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Benutzer vom Betriebssystem authentifiziert werden sollen. Diese Option ermöglicht es [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , Sicherheitsfunktionen von Windows, z. B. die Kennwortverschlüsselung, für die Authentifizierung von Benutzern zu verwenden. Es wird nachdrücklich empfohlen, diese Option auszuwählen.  
  
    -   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentifizierung: Wählen Sie diese Option, wenn Sie möchten, dass Benutzer verwenden ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Anmeldekonto, die Sie erstellt haben. Die Benutzer müssen einen gültigen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldenamen und ein Kennwort angeben.  
  
        > [!CAUTION]  
        >  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-create-a-report-model-using-report-manager"></a>So erstellen Sie ein Berichtsmodell mit dem Berichts-Manager  
  
1.  Wählen Sie im Berichts-Manager die Datenquelle aus, die Sie für das Modell verwenden möchten.  
  
     Die Eigenschaftenseite wird angezeigt.  
  
2.  Überprüfen Sie, ob Sie Optionen verwenden möchten, die für die Datenquelle angegeben wurden.  
  
3.  Klicken Sie auf **Modell generieren**.  
  
     Die Seite Allgemein für die Datenquelle wird angezeigt.  
  
4.  Geben Sie im Feld **Name** einen Namen für das Berichtsmodell ein.  
  
5.  Geben Sie im Feld **Beschreibung** eine kurze Beschreibung des Modells ein.  
  
6.  Klicken Sie auf **Speicherort ändern**, um einen neuen Speicherort für das Berichtsmodell anzugeben.  
  
     Standardmäßig wird das Berichtsmodell im Stammordner des Berichts-Managers gespeichert.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Das Berichtsmodell wird erstellt und in dem von Ihnen angegebenen Ordner gespeichert. Sie können diesem Modell Berechtigungen mit dem Berichts-Manager zuweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](security/granting-permissions-on-a-native-mode-report-server.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Neue Datenquelle (Seite, Berichts-Manager)](../../2014/reporting-services/new-data-source-page-report-manager.md)  
  
  