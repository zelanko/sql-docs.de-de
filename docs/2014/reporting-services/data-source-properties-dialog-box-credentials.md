---
title: Dialogfeld "Eigenschaften", "Anmeldeinformationen für Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.credentials.f1
- "10100"
ms.assetid: 14c3eeb6-d37b-4fda-967b-43afcdb48119
caps.latest.revision: 38
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e8ef67e673e6ba5fe21180c33c8dd501f1baa0c6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280756"
---
# <a name="data-source-properties-dialog-box-credentials"></a>Datenquelleneigenschaften (Dialogfeld), Anmeldeinformationen
  Wählen Sie im Dialogfeld **Datenquelleneigenschaften** die Option **Anmeldeinformationen** aus, um die Anmeldeinformationen für eine Datenquelle im Bericht anzuzeigen und zu ändern. Die von Ihnen bereitgestellten Anmeldeinformationen werden für den Zugriff auf die Datenquelle und zum Zwischenspeichern einer Kopie der Daten für die Berichtsvorschau verwendet. Weitere Informationen dazu, wie Vorschaudaten zwischengespeichert werden, finden Sie unter [Ausführen einer Vorschau für Berichte](reports/previewing-reports.md). Weitere Anmeldeinformationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
## <a name="options"></a>Tastatur  
 **Verwenden Sie Windows-Authentifizierung (integrierte Sicherheit)**  
 Wählen Sie diese Option aus, um die Windows-Authentifizierung zu verwenden.  
  
 **Verwenden Sie diesen Benutzernamen und Kennwort**  
 Wählen Sie diese Option aus, um einen bestimmten Benutzernamen und ein bestimmtes Kennwort bereitzustellen. Für freigegebene Datenquellen gilt Folgendes: Wenn Sie das Berichtsserverprojekt auf dem Zielserver veröffentlichen, werden der Benutzername und das Kennwort als gespeicherte Anmeldeinformationen für die Datenbank gesichert. Wenn Sie den Benutzernamen und das Kennwort als Windows-Anmeldeinformationen verwenden möchten, können Sie die Eigenschaften für die veröffentlichte freigegebene Datenquelle auf dem Zielserver bearbeiten. Weitere Informationen finden Sie unter [Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen ein, der beim Anmelden an der Datenquelle verwendet werden soll.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein, das beim Anmelden an der Datenquelle verwendet werden soll.  
  
 **Eingabeaufforderung für Anmeldeinformationen**  
 Wählen Sie diese Option aus, um beim Ausführen des Berichts Anmeldeinformationen anzufordern.  
  
 **Eingabeaufforderungs-Zeichenfolge eingeben**  
 Geben Sie einen Satz ein, mit dem der Benutzer zur Eingabe von Anmeldeinformationen für die Datenquelle aufgefordert wird.  
  
 **Keine Anmeldeinformationen**  
 Wählen Sie diese Option aus, wenn keine Anmeldeinformationen für die Datenquelle bereitgestellt werden sollen. Diese Option kann nur verwendet werden, wenn die Datenquelle keine Anmeldeinformationen annimmt oder wenn Sie Anmeldeinformationen auf andere Art übergeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Source Dialogfeld, Allgemein](../../2014/reporting-services/data-source-properties-dialog-box-general.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
