---
title: Datenquelle im Dialogfeld Eigenschaften von Anmeldeinformationen (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6798be8db7597de1d4c8d8542fcb6abc8621606
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63165124"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a>Datenquelleigenschaften (Dialogfeld), Anmeldeinformationen (Berichts-Generator)
  Wählen Sie im Dialogfeld **Datenquelleneigenschaften** die Option **Anmeldeinformationen** aus, um die Anmeldeinformationen für eine eingebettete Datenquelle im Bericht anzuzeigen und zu ändern. Die von Ihnen bereitgestellten Anmeldeinformationen werden für den Zugriff auf die Datenquelle für die Berichtsvorschau verwendet. Weitere Informationen zu Anmeldeinformationen finden Sie unter [Angeben von Anmeldeinformationen im Berichts-Generator](../../2014/reporting-services/specify-credentials-in-report-builder.md).  
  
## <a name="options"></a>Optionen  
 **Verwenden Sie Windows-Authentifizierung (integrierte Sicherheit)**  
 Wählen Sie diese Option aus, um die Windows-Authentifizierung zu verwenden.  
  
 **Verwenden Sie diesen Benutzernamen und Kennwort**  
 Wählen Sie diese Option aus, um einen bestimmten Benutzernamen und ein bestimmtes Kennwort bereitzustellen. Für eingebettete Datenquellen gilt Folgendes: Wenn Sie das Berichtsserverprojekt auf dem Zielserver veröffentlichen, werden der Benutzername und das Kennwort als gespeicherte Anmeldeinformationen für die Datenbank gesichert. Wenn Sie den Benutzernamen und das Kennwort als Windows-Anmeldeinformationen verwenden möchten, können Sie die Eigenschaften für die veröffentlichte freigegebene Datenquelle auf dem Zielserver ändern. Weitere Informationen finden Sie unter [Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) in der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dokumentation in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-[Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312).  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen ein, um sich bei der Datenquelle anzumelden.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein, um sich bei der Datenquelle anzumelden.  
  
 **Eingabeaufforderung für Anmeldeinformationen**  
 Aktivieren Sie diese Option, um beim Ausführen des Berichts eine Aufforderung zur Eingabe von Anmeldeinformationen anzuzeigen.  
  
 **Eingabeaufforderungs-Zeichenfolge eingeben**  
 Geben Sie einen Satz ein, mit dem der Benutzer zur Eingabe von Anmeldeinformationen für die Datenquelle aufgefordert wird.  
  
 **Keine Anmeldeinformationen**  
 Wählen Sie diese Option aus, wenn keine Anmeldeinformationen für die Datenquelle bereitgestellt werden sollen. Diese Option kann nur verwendet werden, wenn die Datenquelle keine Anmeldeinformationen annimmt oder wenn Sie Anmeldeinformationen auf andere Art übergeben.  
  
 Bei einigen Datenerweiterungen muss das Konto für die unbeaufsichtigte Ausführung auf dem Berichtsserver konfiguriert werden.  
  
 Weitere Informationen finden Sie im Thema für die entsprechenden Datenquelle in [Hinzufügen von Daten aus externen Datenquellen &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) und [Konfigurieren des unbeaufsichtigten Ausführungskontos &#40;SSRS-Konfigurations-Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dokumentation in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-[Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=121312).  
  
## <a name="see-also"></a>Siehe auch  
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Datenquelleneigenschaften-Dialogfeld, Allgemein (Berichts-Generator)](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md)   
 [Hinzufügen und Prüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
