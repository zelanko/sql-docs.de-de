---
title: Anfügen einer Domäne oder Verbund Domäne an Verweis Daten
description: Beschreibt das Anfügen von Domänen oder Verbund Domänen in einer Data Quality-Wissensdatenbank mit Data Quality Services (DQS) auf SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dm.refdata.f1
- sql13.dqs.dm.refcatalog.f1
ms.assetid: 36af981c-d0d0-4dc6-afe5-bbb3c97845dc
author: swinarko
ms.author: sawinark
ms.openlocfilehash: df671e83d80175f154a4008270c3b68dc2581b59
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75557915"
---
# <a name="attach-domain-or-composite-domain-to-reference-data---data-quality-services-dqs"></a>Anfügen einer Domäne oder Verbund Domäne an Verweis Daten-Data Quality Services (DQS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Thema wird beschrieben, wie Domänen/Verbund Domänen in einer Data Quality-Wissensdatenbank an einen Verweis Datendienst in Azure Marketplace angefügt werden, um Wissen mit qualitativ hochwertigen Verweis Daten zu erstellen. Jeder Verweisdatendienst enthält ein Schema (Datenspalten). Nachdem eine Domäne oder eine Verbunddomäne an einen Verweisdatendienst angefügt wurde, müssen Sie die angefügte Domäne bzw. die einzelnen Domänen innerhalb der Verbunddomäne den entsprechenden Spalten im Schema des Verweisdatendiensts zuordnen. Indem eine Verbunddomäne an einen Verweisdatendienst angefügt wird, haben Sie die Möglichkeit, nur eine Domäne an einen Verweisdatendienst anzufügen. Daraufhin können Sie den entsprechenden Spalten im Schema des Verweisdatendiensts die einzelnen Domänen innerhalb der Verbunddomäne zuordnen.  

> [!IMPORTANT]
> In diesem Artikel werden Referenzdatendienste von Drittanbietern erwähnt, die zuvor in Azure DataMarket verfügbar waren. DataMarket und Data Services – einschließlich z.B. Melissa-Adressdaten – wurden am 31.12.2016 eingestellt. Daher können Sie die Beispiele in diesem Artikel nicht mehr mit den angegebenen Diensten von DataMarket ausführen. Sie können weiterhin Referenzdatendienste nutzen, die von externen Referenzdatenanbietern direkt online angeboten werden.

> [!WARNING]  
>  Die an einen Verweisdatendienst angefügte Verbunddomäne ist in der Domänen-Dropdownliste verfügbar, während Domänen den Spalten in Schema des Verweisdatendiensts zugeordnet werden. Ordnen Sie die Verbunddomäne keiner Spalte im Schema des Verweisdatendiensts zu; Sie dürfen den entsprechenden Spalten im Schema des Verweisdatendiensts nur einzelne Domänen innerhalb einer Verbunddomäne zuordnen. Andernfalls tritt ein Fehler auf.  
  
 Das Schema eines Verweisdatendiensts kann über eine erforderliche Spalte verfügen, die mit der entsprechenden Domäne zugeordnet werden muss, wenn Sie einen Verweisdatendienst verwenden möchten. Die erforderliche Spalte in einem Verweisdatenschema wird mit einem „(M)“ im Spaltennamen gekennzeichnet. So ist **AddressLine** beispielsweise die erforderliche Schemaspalte in **Melissa Data (Adressdaten)**, und **CompanyName** ist die erforderliche Schemaspalte in **Digital Trowel Inc. (US-Unternehmen und professionelle Daten für SQL-Benutzer)**.  
  
 In diesem Thema erstellen wir vier Domänen: **Adresszeile**, **Ort**, **Bundesland** und **PLZ**, unter einer Verbunddomäne, **Adressüberprüfung**, fügen die Verbunddomäne an den Verweisdatendienst **Melissa Data (Adressüberprüfung)** an und ordnen die einzelnen Domänen innerhalb der Verbunddomäne anschließend den entsprechenden Spalten im Schema des Verweisdatendiensts zu.  
  
## <a name="before-you-begin"></a>Voraussetzungen  
  
###  <a name="Prerequisites"></a>Voraussetzung  
 Sie müssen [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) konfiguriert haben, um Verweisdatendienste zu verwenden. Siehe [Konfigurieren von DQS zum Verwenden von Verweisdaten](../data-quality-services/configure-dqs-to-use-reference-data.md).  
  
###  <a name="Security"></a>Sicherung  
  
#### <a name="permissions"></a>Berechtigungen  
 Sie müssen über die dqs_kb_editor-Rolle in der DQS_MAIN-Datenbank verfügen, um Domänen Verweisdaten zuzuordnen.  
  
##  <a name="Map"></a>Zuordnen von Domänen zu Verweis Daten aus Melissa Data  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm unter **Wissensdatenbank-Verwaltung**auf **Neue Wissensdatenbank**.  
  
3.  Geben Sie im Bildschirm **Neue Wissensdatenbank** einen Namen für die neue Wissensdatenbank ein, klicken Sie auf die Aktivität **Domänenverwaltung** , und klicken Sie auf **Erstellen**.  
  
4.  Klicken Sie im Bildschirm **Domänenverwaltung** auf das Symbol **Domäne erstellen** , um eine Domäne zu erstellen. Erstellen Sie die folgenden vier Domänen: **Adresszeile**, **Ort**, **Bundesland**und **PLZ**.  
  
5.  Klicken Sie auf das Symbol **Verbunddomäne erstellen** , um eine Verbunddomäne zu erstellen. Geben Sie im Dialogfeld **Verbunddomäne erstellen** im Feld **Name der Verbunddomäne** den Text **Adressenüberprüfung** ein, und schließen Sie alle Domänen ein, die unter Schritt 3 in der Verbunddomäne erstellt wurden. Klicken Sie auf **OK**.  
  
6.  Wählen Sie im Bereich **Domäne** auf der linken Seite die Verbunddomäne aus, indem Sie auf **Adressenüberprüfung**klicken, und klicken Sie dann auf der rechten Seite auf die Registerkarte **Verweisdaten** .  
  
7.  Klicken Sie auf das Symbol **Durchsuchen** .  
  
8.  Im Dialogfeld **Onlinekatalog der Reference Data Service-Anbieter** :  
  
    1.  Aktivieren Sie unter **DataMarket Data Quality Services** das Kontrollkästchen **Melissa Data (Adressüberprüfung)**.  
  
    2.  Ordnen Sie die Spalten des Verweisdatendiensts Melissa Data (Adressüberprüfung) den entsprechenden Domänen (Adresszeile, Ort, Bundesland und PLZ) zu. Sie ordnen die Spalten zu, indem Sie in der Spalte **RDS-Schema** eine Verweisdatendienst-Spalte auswählen und dann die entsprechende Domäne in der Spalte **Domäne** auswählen. Um mehr Zeilen in der Tabelle hinzuzufügen, klicken Sie auf das Symbol **Schemaeintrag hinzufügen** .  
  
    3.  Klicken Sie auf **OK** , um die Änderungen zu speichern, und schließen Sie das Dialogfeld **Onlinekatalog der Reference Data Service-Anbieter** .  
  
         ![Dialogfeld "Onlinekatalog der Reference Data Service-Anbieter"](../data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "Dialogfeld "Onlinekatalog der Reference Data Service-Anbieter"")  
  
        > [!NOTE]  
        >  -   Im Dialogfeld **Online Katalog der Verweis Datenanbieter** zeigt der Knoten **datamarket Data Quality Services** alle Reference Data Service-Anbieter an, die Sie in Azure Marketplace abonniert haben. Wenn Sie in DQS direkte Drittanbieter von Online-Verweisdatendiensten konfiguriert haben, werden diese unter einem anderen Knoten mit der Bezeichnung **Direkte Drittanbieter-Onlineanbieter** angezeigt (zu diesem Zeitpunkt nicht verfügbar, da keine direkten Drittanbieter von Online-Verweisdatendiensten in DQS konfiguriert sind).  
  
9. Sie kehren zur Registerkarte **Verweis Daten** zurück. Ändern Sie im Bereich **Anbieter Einstellungen** ggf. die Werte in den folgenden Feldern:  
  
    -   **Schwellenwert für die automatische Korrektur**: Korrekturen aus dem Verweis Datendienst mit einem Vertrauensgrad oberhalb dieses Schwellenwerts werden automatisch durchgeführt. Geben Sie einen Wert in der Dezimalnotation des entsprechenden Prozentwerts ein. Geben Sie beispielsweise 0,9 für 90 % ein.  
  
    -   **Vorgeschlagene Kandidaten**: Anzahl der vorgeschlagenen Kandidaten, die vom Verweis Datendienst angezeigt werden sollen.  
  
    -   Minimaler **Vertrauens**Grad: Vorschläge aus dem Verweis Datendienst mit einem Vertrauensgrad, der niedriger als dieser Wert ist, werden ignoriert. Geben Sie einen Wert in der Dezimalnotation des entsprechenden Prozentwerts ein. Geben Sie beispielsweise 0,6 für 60 % an.  
  
10. Klicken Sie auf **Fertig stellen** , um die Wissensdatenbank zu veröffentlichen. Eine Bestätigungsmeldung wird angezeigt, nachdem die Wissensdatenbank erfolgreich veröffentlicht wurde.  
  
 Sie können diese Wissensdatenbank jetzt für Bereinigungs Aktivitäten in einem Data Quality-Projekt verwenden, um US-Adressen in den Quelldaten zu standardisieren und zu bereinigen, basierend auf den von Melissa Data über Azure Marketplace bereitgestellten Kenntnissen.  
  
##  <a name="FollowUp"></a>Nachverfolgung: nach dem Mapping einer Domäne zu Verweis Daten  
 Erstellen Sie ein Data Quality-Projekt, und führen Sie die Bereinigungsaktivität für die Quelldaten aus, die US-Adressen enthalten, indem Sie diese mit der in diesem Thema erstellten Wissensdatenbank vergleichen. Siehe [Bereinigen von Daten mit Wissen über &#40;externe&#41; Verweisdaten](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verweis Data Services in DQS](../data-quality-services/reference-data-services-in-dqs.md)   
 [Datenbereinigung](../data-quality-services/data-cleansing.md)  
  
  
