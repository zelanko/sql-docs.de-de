---
title: Installieren von SCOM-Management Packs
description: Führen Sie die folgenden Schritte aus, um die System Center Operations Manager-Management Packs (SCOM) für SQL Server PDW herunterzuladen und zu installieren. Die Management Packs sind erforderlich, um SQL Server PDW von SCOM zu überwachen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: f3652b767f4628b61f5dd363999838418ff933aa
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401074"
---
# <a name="install-sql-server-operations-manager-scom-management-packs-for-analytics-platform-system"></a>Installieren von SQL Server Operations Manager Management Packs (SCOM) für Analytics Platform System
Führen Sie die folgenden Schritte aus, um die System Center Operations Manager-Management Packs (SCOM) für SQL Server PDW herunterzuladen und zu installieren. Die Management Packs sind erforderlich, um SQL Server PDW von SCOM zu überwachen.  
  
## <a name="BeforeBegin"></a>Bevor Sie beginnen  
**Voraussetzungen**  
  
System Center Operations Manager müssen installiert sein und ausgeführt werden. SQL Server PDW 2012 erfordert System Center Operations Manager 2007 R2, System Center Operations Manager 2012 oder System Center Operations Manager 2012 Service Pack 1.  
  
## <a name="Step1"></a>Schritt 1: Herunterladen der Management Packs  
Laden Sie für die APS PDW-Arbeitsauslastung das [System Center-Management Pack für den Microsoft Analytics Platform System](https://go.microsoft.com/fwlink/?LinkId=396857)herunter.  
  
Laden Sie für die Geräteverwaltung das [Basis-Management Pack für SQL Server Appliance](https://docs.microsoft.com/previous-versions/system-center/packs/gg602398(v=technet.10))herunter.  
  
Für ältere Versionen von PDW ohne APS laden Sie das[System Center Monitoring Pack für Microsoft SQL Server 2012 parallel Data Warehouse Appliance](https://go.microsoft.com/fwlink/p/?LinkId=282661)herunter.  
  
<!-- MISSING LINKS - For the HDInsight workload, download the [System Center Management Pack for HDInsight](https://go.microsoft.com/fwlink/?LinkId=390208).  -->
  
## <a name="Step2"></a>Schritt 2: Installieren der Management Packs  
  
### <a name="install-the-sql-server-appliance-base-management-pack"></a>Installieren des Basis-Management Packs für die SQL Server Appliance  
  
1.  Zum Ausführen der Installation Doppelklicken Sie auf das heruntergeladene Basis-Management Pack für SQL Server Appliance.  
  
2.  Akzeptieren Sie den Lizenzvertrag, und klicken Sie auf **weiter**.  
  
    ![Akzeptieren Sie den Lizenzvertrag.](./media/install-the-scom-management-packs/SCOM_licnse_agrmt.png "SCOM_licnse_agrmt")  
  
3.  Wählen Sie Ihren eigenen Installationsordner aus, oder verwenden Sie den Standard-Management Pack-Installationsordner.  
  
    ![Installationsordner auswählen](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
4.  Klicken Sie auf **Installieren**.  
  
    ![Bestätigen der Installation](./media/install-the-scom-management-packs/SCOM_licnse_agrmt3.png "SCOM_licnse_agrmt3")  
  
5.  Klicken Sie auf **Schließen**.  
  
    ![Klicken Sie auf Schließen](./media/install-the-scom-management-packs/SCOM_licnse_agrmt4.png "SCOM_licnse_agrmt4")  
  
### <a name="install-the-monitoring-pack-for-sql-server-pdw-appliance"></a>Installieren des Überwachungs Pakets für SQL Server PDW Appliance  
  
1.  Zum Ausführen der Installation Doppelklicken Sie auf das heruntergeladene SQL Server PDW Appliance-Management Pack.  
  
2.  Akzeptieren Sie den Lizenzvertrag, und klicken Sie auf **weiter**.  
  
    ![Akzeptieren der Lizenzbedingungen](./media/install-the-scom-management-packs/SCOM_licnse_agmtB.png "SCOM_licnse_agmtB")  
  
3.  Wählen Sie das Verzeichnis aus, in dem die extrahierten Dateien gespeichert werden. Standardmäßig wird der Standard-Management Pack-Installationsordner angezeigt. Wählen Sie den Standardwert aus, oder wählen Sie einen eigenen Installationsordner aus.  
  
    ![Installationsordner auswählen](./media/install-the-scom-management-packs/SCOM_licnse_agmtB1.png "SCOM_licnse_agmtB1")  
  
4.  Klicken Sie auf **Installieren**.  
  
    ![Bestätigen der Installation](./media/install-the-scom-management-packs/SCOM_licnse_agmtB2.png "SCOM_licnse_agmtB2")  
  
5.  Klicken Sie auf **Schließen**.  
  
    ![Installation ist beendet](./media/install-the-scom-management-packs/SCOM_licnse_agmtB3.png "SCOM_licnse_agmtB3")  
  
## <a name="next-step"></a>Nächster Schritt  
Nachdem Sie die Management Packs installiert haben, fahren Sie mit dem nächsten Schritt fort: [Importieren des SCOM-Management Packs für PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
