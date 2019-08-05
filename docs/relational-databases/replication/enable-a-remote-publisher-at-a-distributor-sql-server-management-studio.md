---
title: Aktivieren eines Remoteverlegers auf einem Verteiler (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: ccf53893db8de9e80a1c8545dfe7a5af1819a6a7
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768535"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a>Aktivieren eines Remoteverlegers auf einem Verteiler (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Auf der Seite **Verleger** können Sie aktivieren, dass ein Verleger einen Remoteverteiler verwendet. Diese Seite ist im Assistenten für Verteilungskonfiguration sowie über das Dialogfeld **Verteilereigenschaften - \<Verteiler>** verfügbar. Weitere Informationen zum Verwenden des Assistenten sowie zum Zugriff auf das Dialogfeld finden Sie unter [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md) und [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a>So aktivieren Sie einen Verleger im Verteilungskonfigurations-Assistenten  
  
1.  Klicken Sie im Verteilungskonfigurations-Assistenten auf der Seite **Verleger** auf **Hinzufügen**.  
  
2.  Klicken Sie auf **SQL Server-Verleger hinzufügen**. Informationen zum Aktivieren der Verwendung eines Verteilers auf einem Oracle-Verleger finden Sie unter [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** die Verbindungsinformationen für den Verleger an, der den Remoteverteiler verwenden soll, und klicken Sie anschließend auf **Verbinden**.  
  
4.  Geben Sie auf der Seite **Verteilerkennwort** in den Textfeldern **Kennwort** und **Kennwort bestätigen** ein sicheres Kennwort für das **distributor_admin** -Konto an, das die Replikation zum Herstellen der Verbindung zwischen dem Verleger und dem Verteiler verwendet, um administrative Aufgaben auszuführen.  
  
5.  Klicken Sie auf die Schaltfläche mit den drei Punkten ( **…** ), um die Einstellungen eines Verlegers anzuzeigen und zu ändern.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a>So aktivieren Sie einen Verleger im Dialogfeld "Verteilereigenschaften"  
  
1.  Klicken Sie auf der Seite **Verleger** des Dialogfelds **Verteilereigenschaften - \<Verteiler>** auf **Hinzufügen**.  
  
2.  Klicken Sie auf **SQL Server-Verleger hinzufügen**. Informationen zum Aktivieren der Verwendung eines Verteilers auf einem Oracle-Verleger finden Sie unter [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  Geben Sie im Dialogfeld **Verbindung mit Server herstellen** die Verbindungsinformationen für den Verleger an, der den Remoteverteiler verwenden soll, und klicken Sie anschließend auf **Verbinden**.  
  
4.  Geben Sie auf der Seite **Verleger** in den Textfeldern **Kennwort** und **Kennwort bestätigen** ein sicheres Kennwort für das **distributor_admin** -Konto an, das die Replikation zum Herstellen der Verbindung zwischen dem Verleger und dem Verteiler verwendet, um administrative Aufgaben auszuführen.  
  
5.  Klicken Sie auf die Schaltfläche mit den drei Punkten ( **…** ), um die Einstellungen eines Verlegers anzuzeigen und zu ändern.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)   
 [Schützen des Verteilers](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  
