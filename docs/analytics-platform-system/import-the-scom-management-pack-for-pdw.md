---
title: Importieren Sie SCOM Management Pack - Analytics Platform System | Microsoft-Dokumentation
description: Um die System Center Operations Manager (SCOM) Management Packs für Analytics Platform System (APS) importieren, gehen Sie wie folgt vor. Die Management Packs müssen Parallel Data Warehouse von SCOM überwacht.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 070e7b73614f6884e45a5c91603d6086613d15ca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960857"
---
# <a name="import-the-scom-management-pack---analytics-platform-system"></a>Importieren Sie das SCOM-Management Pack - Analytics Platform System
Um die System Center Operations Manager (SCOM) Management Packs für Analytics Platform System (APS) importieren, gehen Sie wie folgt vor. Die Management Packs müssen Parallel Data Warehouse von SCOM überwacht. 
  
## <a name="BeforeBegin"></a>Vorbereitungen  
**Erforderliche Komponenten**  
  
System Center Operationsmanager 2007 R2 muss installiert und ausgeführt werden.  
  
Die Management Packs müssen installiert sein. Finden Sie unter [die SCOM-Management Packs &#40;Analytics-Plattformsystem&#41;](install-the-scom-management-packs.md).  
  
## <a name="Step1"></a>Schritt 1: Importieren Sie das SQL Server-Gerät-Basis-Management Pack  
  
1.  Melden Sie sich beim Computer mit einem Konto, ein Mitglied der Operations Manager-Administratorrolle für die Operations Manager 2007-Verwaltungsgruppe ist.  
  
2.  Klicken Sie in der Betriebskonsole auf **Verwaltung**.  
  
3.  Mit der rechten Maustaste die **Management Packs** Knoten, und klicken Sie dann auf **Management Packs importieren**.  
  
    ![Klicken Sie auf Management Packs importieren](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM")  
  
4.  Wählen Sie in der Liste der Management Packs das Management Pack, das Sie importieren möchten, klicken Sie auf **wählen**, und klicken Sie dann auf **hinzufügen**.  
  
    ![Liste der Management Packs](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  Suchen Sie nach **Appliance** und danach einen Drilldown in SQL Server-Gerät-Basis, und klicken Sie dann auf **hinzufügen** die beiden Optionen.  
  
    ![SQL Server-Anwendungsbasis](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  Nachdem Sie unten im ausgewählten Bereich der beiden Management Packs wurden, klicken Sie dann auf **OK**.  
  
    ![Auswählen beider Management Packs](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  Klicken Sie auf **Installieren**.  
  
    ![Klicken Sie auf Installieren](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  Klicken Sie abschließend auf **schließen**.  
  
    ![Sobald der Vorgang abgeschlossen ist, klicken Sie auf Schließen](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Importieren Sie das Überwachungspaket für Microsoft SQL Server 2008 R2 Parallel Data Warehouse-Appliance  
  
1.  Mit der rechten Maustaste die **Management Packs** Knoten, und klicken Sie dann auf **Management Packs importieren**.  
  
2.  Wählen Sie **von Datenträger hinzufügen**...  
  
    ![Mit der rechten Maustaste in Management Packs](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  Wechseln Sie zu dem Speicherort, in dem Sie die SQL Server PDW-Management Packs extrahiert, und wählen Sie die drei Management Packs, die im Abschnitt "Ausgewählte Management packs importieren" sind. Dies ist möglich, indem Sie die erste Vorlage, UMSCHALT auf und die letzte Vorlage. Nachdem sie alle ausgewählt sind, klicken Sie auf **öffnen**.  
  
    ![Management Packs auswählen](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  Klicken Sie auf **Installieren**.  
  
    ![Klicken Sie auf Installieren](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Klicken Sie auf **Schließen**.  
  
    ![Klicken Sie auf Schließen](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>Nächster Schritt  
Nun, da Sie die Management Packs importiert haben, fahren Sie mit dem nächsten Schritt fort: [Konfiguration von SCOM zum Überwachen von Analytics-Plattformsystem &#40;Analytics-Plattformsystem&#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
