---
title: Eigenschaften der freigegebenen Datenquelle (Dialog Feld), Anmelde Informationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shareddatasource.credentials.f1
ms.assetid: c08d1a5f-206b-4d53-ab1a-368b651ee5bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cf21cc35bb41837b65d2a2b3c2c946ffae34864f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101263"
---
# <a name="shared-data-source-properties-dialog-box-credentials"></a>Eigenschaften der freigegebenen Datenquelle (Dialogfeld), Anmeldeinformationen
  Wählen Sie im Dialogfeld **Eigenschaften der freigegebenen Datenquelle** die Option **Anmeldeinformationen** aus, um die Anmeldeinformationen für eine freigegebene Datenquelle im Bericht anzuzeigen und zu ändern. Die von Ihnen bereitgestellten Anmeldeinformationen werden für den Zugriff auf die Datenquelle und zum Zwischenspeichern einer Kopie der Daten für die Berichtsvorschau verwendet. Weitere Informationen dazu, wie Vorschaudaten zwischengespeichert werden, finden Sie unter [Ausführen einer Vorschau für Berichte](reports/previewing-reports.md). Weitere Anmeldeinformationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
## <a name="options"></a>Tastatur  
 **Windows-Authentifizierung verwenden (Integrierte Sicherheit)**  
 Wählen Sie diese Option aus, um die Windows-Authentifizierung zu verwenden.  
  
 **Diesen Benutzernamen und dieses Kennwort verwenden**  
 Wählen Sie diese Option aus, um einen bestimmten Benutzernamen und ein bestimmtes Kennwort bereitzustellen. Für freigegebene Datenquellen gilt Folgendes: Wenn Sie das Berichtsserverprojekt auf dem Zielserver veröffentlichen, werden der Benutzername und das Kennwort als gespeicherte Anmeldeinformationen für die Datenbank gesichert. Wenn Sie den Benutzernamen und das Kennwort als Windows-Anmeldeinformationen verwenden möchten, können Sie die Eigenschaften für die veröffentlichte freigegebene Datenquelle auf dem Zielserver bearbeiten. Weitere Informationen finden Sie unter [Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen ein, der beim Anmelden an der Datenquelle verwendet werden soll.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein, das beim Anmelden an der Datenquelle verwendet werden soll.  
  
 **Aufforderung zur Eingabe von Anmeldeinformationen**  
 Wählen Sie diese Option aus, um beim Ausführen des Berichts Anmeldeinformationen anzufordern.  
  
 **Eingabeaufforderungs-Zeichenfolge eingeben**  
 Geben Sie einen Satz ein, mit dem der Benutzer zur Eingabe von Anmeldeinformationen für die Datenquelle aufgefordert wird.  
  
 **Keine Anmeldeinformationen**  
 Wählen Sie diese Option aus, wenn keine Anmeldeinformationen für die Datenquelle bereitgestellt werden sollen. Diese Option kann nur verwendet werden, wenn die Datenquelle keine Anmeldeinformationen annimmt oder wenn Sie Anmeldeinformationen auf andere Art übergeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Angeben von Anmelde Informationen und Verbindungsinformationen für Berichtsdaten Quellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Eigenschaften der freigegebenen Datenquelle (Dialogfeld), Allgemein](../../2014/reporting-services/shared-data-source-properties-dialog-box-general.md)  
  
  
