---
title: SCOM-Management Pack importieren
description: Führen Sie die folgenden Schritte aus, um die System Center Operations Manager (SCOM) Management Packs für Analytics Platform System (APS) zu importieren. Die Management Packs sind zum Überwachen paralleler Data Warehouse von SCOM erforderlich.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: bcb0e667424767fd53a5fc7e027e84d512022203
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401086"
---
# <a name="import-the-scom-management-pack---analytics-platform-system"></a>Importieren Sie das SCOM Management Pack-Analytics Platform System.
Führen Sie die folgenden Schritte aus, um die System Center Operations Manager (SCOM) Management Packs für Analytics Platform System (APS) zu importieren. Die Management Packs sind zum Überwachen paralleler Data Warehouse von SCOM erforderlich. 
  
## <a name="BeforeBegin"></a>Bevor Sie beginnen  
**Voraussetzungen**  
  
System Center Operations Manager 2007 R2 muss installiert sein und ausgeführt werden.  
  
Die Management Packs müssen installiert sein. Weitere Informationen finden Sie [unter Installieren der SCOM-Management Packs &#40;Analytics Platform System&#41;](install-the-scom-management-packs.md).  
  
## <a name="Step1"></a>Schritt 1: Importieren des Basis-Management Packs für die SQL Server Appliance  
  
1.  Melden Sie sich am Computer mit einem Konto an, das Mitglied der Rolle "Operations Manager-Administratoren" für die Operations Manager 2007-Verwaltungsgruppe ist.  
  
2.  Klicken Sie in der Betriebskonsole auf **Verwaltung**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Knoten **Management Packs** , und klicken Sie dann auf **Management Packs importieren**.  
  
    ![Klicken auf 'Management Packs importieren'](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM_IMP")  
  
4.  Wählen Sie in der Liste der Management Packs die Management Pack aus, die Sie importieren möchten, klicken Sie auf **auswählen**, und klicken Sie dann auf **Hinzufügen**.  
  
    ![Management Pack-Liste](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  Suchen Sie nach **Appliance** , und führen Sie einen Drilldown in SQL Server Appliance Base aus, **und klicken Sie** dann auf die beiden Optionen.  
  
    ![SQL Server-Anwendungsbasis](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  Nachdem Sie die beiden Management Packs im unteren Bereich ausgewählt haben, klicken Sie auf **OK**.  
  
    ![Auswählen beider Management Packs](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  Klicken Sie auf **Installieren**.  
  
    ![Klicken Sie auf Installieren](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  Klicken Sie nach Abschluss **des**Vorgangs auf schließen.  
  
    ![Klicken auf 'Schließen' nach Abschluss](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Importieren Sie das Überwachungspaket für Microsoft SQL Server 2008 R2 parallel Data Warehouse Appliance  
  
1.  Klicken Sie mit der rechten Maustaste auf den Knoten **Management Packs** , und klicken Sie dann auf **Management Packs importieren**.  
  
2.  Wählen Sie von Datenträger **Hinzufügen**... aus.  
  
    ![Rechtsklick auf 'Management Packs'](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  Wechseln Sie zu dem Speicherort, an den Sie die SQL Server PDW Management Packs extrahiert haben, und wählen Sie die drei Management Packs aus, die sich im Abschnitt "ausgewählte Management Packs" befinden. Wählen Sie hierzu das erste aus, klicken Sie auf verschieben, und wählen Sie das letzte aus. Wenn alle ausgewählt sind, klicken Sie auf **Öffnen**.  
  
    ![Management Packs auswählen](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  Klicken Sie auf **Installieren**.  
  
    ![Klicken Sie auf Installieren](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Klicken Sie auf **Schließen**.  
  
    ![Klicken Sie auf Schließen](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>Nächster Schritt  
Nachdem Sie die Management Packs importiert haben, fahren Sie mit dem nächsten Schritt fort: [Konfigurieren von SCOM zum Überwachen von Analytics Platform System &#40;Analytics Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
