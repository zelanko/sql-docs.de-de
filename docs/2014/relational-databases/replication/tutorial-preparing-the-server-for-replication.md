---
title: 'Tutorial: Vorbereiten des Servers für die Replikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8e68be637511fb00774d35b564b0e5ec5979b60d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228240"
---
# <a name="tutorial-preparing-the-server-for-replication"></a>Lernprogramm: Vorbereiten des Servers für die Replikation
  Es ist wichtig, einen Sicherheitsplan zu erstellen, bevor Sie die Replikationstopologie konfigurieren. In diesem Lernprogramm erfahren Sie, wie Sie eine Replikationstopologie besser sichern und die Verteilung konfigurieren können. Dieser Vorgang stellt den ersten Schritt für die Replikation von Daten dar. Es ist erforderlich, dieses Lernprogramm vor allen anderen Lernprogrammen abzuschließen.  
  
> [!NOTE]  
>  Für das sichere Replizieren von Daten zwischen Servern empfiehlt es sich, alle Empfehlungen unter [Bewährte Methoden für die Replikationssicherheit](security/replication-security-best-practices.md)zu implementieren.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie Sie einen Server vorbereiten, sodass die Replikation sicher und mit den geringsten Privilegien ausgeführt werden kann. In der ersten Lektion wird veranschaulicht, wie Sie die Windows-Dienstkonten erstellen können, die zur Ausführung von Replikations-Agents verwendet werden. In der zweiten Lektion erfahren Sie, wie der Ordner konfiguriert wird, in dem Momentaufnahmeveröffentlichungen generiert und gespeichert werden. In der dritten Lektion wird das Konfigurieren der Verteilung und das Festlegen der Berechtigungen erläutert.  
  
## <a name="requirements"></a>Anforderungen  
 Dieses Lernprogramm ist für Benutzer vorgesehen, die mit grundlegenden Datenbankvorgängen vertraut sind, aber nur über begrenzte Erfahrungen in Bezug auf die Replikation verfügen.  
  
 Ihr System muss die folgenden installierten Komponenten aufweisen, damit dieses Lernprogramm verwendet werden kann:  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] mit der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank. Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert.  
  
 **Geschätzte Zeit zum Bearbeiten dieses Lernprogramms: 30 Minuten**  
  
## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm  
  
-   [Lektion 1: Erstellen von Windows-Konten für die Replikation](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [Lektion 2: Vorbereiten des Momentaufnahmeordners](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [Lektion 3: Konfigurieren der Verteilung](lesson-3-configuring-distribution.md)  
  
 [Lernprogramm starten](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Sicherheit und Schutz &#40;Replikation&#41;](security/security-and-protection-replication.md)  
  
  
