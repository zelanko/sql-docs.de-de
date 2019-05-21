---
title: Momentaufnahmeordner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5f8e3050afe889fd1c7f7de489b7ed6d22d3a50f
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133200"
---
# <a name="snapshot-folder"></a>Momentaufnahmeordner
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Seite **Momentaufnahmeordner** wird im Verteilungskonfigurations-Assistenten und im Assistenten für neue Veröffentlichung angezeigt. Der von Ihnen für den Momentaufnahmeordner angegebene Speicherort wird als Standardvorgabe für alle in diesem Assistenten aktivierten Verleger verwendet (der standardmäßige Momentaufnahmeordner gilt nicht für Verleger, die später mithilfe des Dialogfelds **Verteilereigenschaften** aktiviert werden). Sie können diese Standardeinstellung für jeden Verleger auf der Seite **Verleger** des Verteilungskonfigurations-Assistenten oder im Dialogfeld **Verteilereigenschaften** überschreiben.  
  
 Der Momentaufnahmeordner ist lediglich ein von Ihnen freigegebenes Verzeichnis. Agents, die aus diesem Ordner lesen bzw. in den Ordner schreiben, benötigen ausreichende Zugriffsberechtigungen. Weitere Informationen zum Sichern des Ordners finden Sie unter [Sichern des Momentaufnahmeordners](../../relational-databases/replication/security/secure-the-snapshot-folder.md). Testen Sie vor der Implementierung der Replikation, ob die Replikations-Agents eine Verbindung mit dem Momentaufnahmeordner herstellen können. Melden Sie sich unter dem von dem jeweiligen Agenten verwendeten Konto an, und versuchen Sie, auf den Momentaufnahmeordner zuzugreifen.  
  
## <a name="options"></a>Optionen  
 **Snapshot folder**  
 Geben Sie den Pfad für den Ordner an, in dem Momentaufnahmedateien gespeichert werden sollen.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt die Verwendung einer Netzwerkfreigabe als Speicherort des Momentaufnahmeordners. Auf lokale Pfade (beginnend mit einem Laufwerksbuchstaben, z.B. C:\\) können Agents und andere Computer nicht zugreifen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ändern von Momentaufnahmeoptionen](../../relational-databases/replication/snapshot-options.md)   
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)   
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
