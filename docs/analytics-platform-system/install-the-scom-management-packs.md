---
title: Installieren Sie die SCOM-Management-Packs - Analytics Platform System | Microsoft-Dokumentation
description: Führen Sie diese Schritte zum Herunterladen und installieren die System Center Operations Manager (SCOM) Management Packs für SQL Server PDW. Die Management Packs sind zum Überwachen von SQL Server PDW von SCOM erforderlich.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f0acfa636a3432dcffb18cfec57ee7625c1eb01b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63215522"
---
# <a name="install-sql-server-operations-manager-scom-management-packs-for-analytics-platform-system"></a>Installieren von SQL Server Operations Manager (SCOM) Management Packs für Analytics Platform System
Führen Sie diese Schritte zum Herunterladen und installieren die System Center Operations Manager (SCOM) Management Packs für SQL Server PDW. Die Management Packs sind zum Überwachen von SQL Server PDW von SCOM erforderlich.  
  
## <a name="BeforeBegin"></a>Vorbereitungen  
**Erforderliche Komponenten**  
  
System Center Operations Manager muss installiert und ausgeführt werden. SQL Server PDW 2012 erfordert System Center Operations Manager 2007 R2, System Center Operations Manager 2012 oder System Center Operations Manager 2012 Servicepack 1.  
  
## <a name="Step1"></a>Schritt 1: Herunterladen der Management Packs  
Herunterladen der APS-PDW-arbeitsauslastung, die [System Center Management Pack für Microsoft Analytics Platform System](https://go.microsoft.com/fwlink/?LinkId=396857).  
  
Herunterladen für die Verwaltung des Geräts, das [Base Management Pack für SQL Server-Appliance](https://www.microsoft.com/download/details.aspx?displaylang=en&id=11436).  
  
Bei älteren Versionen von PDW ohne APS Herunterladen der[System Center Monitoring Pack für Microsoft SQL Server 2012 Parallel Data Warehouse-Anwendung](https://go.microsoft.com/fwlink/p/?LinkId=282661).  
  
<!-- MISSING LINKS - For the HDInsight workload, download the [System Center Management Pack for HDInsight](https://go.microsoft.com/fwlink/?LinkId=390208).  -->
  
## <a name="Step2"></a>Schritt 2: Die Management Packs  
  
### <a name="install-the-sql-server-appliance-base-management-pack"></a>Installieren Sie das SQL Server-Gerät-Basis-Management Pack  
  
1.  Um die Installation auszuführen, doppelklicken Sie auf das heruntergeladene SQL Server-Appliance Base Management Pack.  
  
2.  Akzeptieren Sie den Lizenzvertrag, und klicken Sie auf **Weiter**.  
  
    ![Akzeptieren der Lizenzbedingungen](./media/install-the-scom-management-packs/SCOM_licnse_agrmt.png "SCOM_licnse_agrmt")  
  
3.  Wählen Sie eigene Installationsordner aus, oder verwenden Sie die Standard-Management Pack Installationsordner.  
  
    ![Installationsordner auswählen](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
4.  Klicken Sie auf **Installieren**.  
  
    ![Installation bestätigen](./media/install-the-scom-management-packs/SCOM_licnse_agrmt3.png "SCOM_licnse_agrmt3")  
  
5.  Klicken Sie auf **Schließen**.  
  
    ![Klicken Sie auf Schließen](./media/install-the-scom-management-packs/SCOM_licnse_agrmt4.png "SCOM_licnse_agrmt4")  
  
### <a name="install-the-monitoring-pack-for-sql-server-pdw-appliance"></a>Installieren Sie das Überwachungspaket für SQL Server-PDW-Anwendung  
  
1.  Um die Installation auszuführen, doppelklicken Sie auf das heruntergeladene SQL Server PDW Appliance Management Pack.  
  
2.  Akzeptieren Sie den Lizenzvertrag, und klicken Sie auf **Weiter**.  
  
    ![Akzeptieren der Lizenzbedingungen](./media/install-the-scom-management-packs/SCOM_licnse_agmtB.png "SCOM_licnse_agmtB")  
  
3.  Wählen Sie das Verzeichnis, das die extrahierten Dateien enthalten wird. Der Standardinstallationsordner für die Management Pack werden standardmäßig angezeigt. Wählen Sie die Standardeinstellung, oder wählen Sie Ihre eigenen Installationsordner.  
  
    ![Auswählen des Installationsordners](./media/install-the-scom-management-packs/SCOM_licnse_agmtB1.png "SCOM_licnse_agmtB1")  
  
4.  Klicken Sie auf **Installieren**.  
  
    ![Installation bestätigen](./media/install-the-scom-management-packs/SCOM_licnse_agmtB2.png "SCOM_licnse_agmtB2")  
  
5.  Klicken Sie auf **Schließen**.  
  
    ![Installation abgeschlossen](./media/install-the-scom-management-packs/SCOM_licnse_agmtB3.png "SCOM_licnse_agmtB3")  
  
## <a name="next-step"></a>Nächster Schritt  
Nun, da Sie die Management Packs installiert haben, fahren Sie mit dem nächsten Schritt fort: [Importieren des SCOM Management Packs für PDW &#40;Analytics-Plattformsystem&#41;](import-the-scom-management-pack-for-pdw.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
