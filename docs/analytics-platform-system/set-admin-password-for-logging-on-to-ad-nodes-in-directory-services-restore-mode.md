---
title: Legen Sie Active Directory-Kennwort - Analytics Platform System | Microsoft-Dokumentation
description: Legen Sie Active Directory-Knoten-Administrator-Anmeldekennwort, in den Wiederherstellungsmodus für Verzeichnisdienste in Analytics Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 277f2b8195aa4238a490d37faaf81abdafc0008c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538745"
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>Festlegen des Administratorkennworts für die Anmeldung bei AD-Knoten im Verzeichnisdienste-Wiederherstellungsmodus (DSRM) - Analytics Platform System
Directory Verzeichnisdienst-Wiederherstellungsmodus (DSRM) ist eine Startmodus zum Reparieren oder Wiederherstellen von Active Directory Domain Services (AD DS). Es wird verwendet, mit der AD-applianceknoten anmelden können, nach einem Fehler bei AD DS oder AD DS muss wiederhergestellt werden. Das Kennwort für den Verzeichnisdienst-Wiederherstellungsmodus wurde während des Setups Appliance am Standort Hardware-Hersteller initialisiert und sollte durch den Administrator der Anwendung geändert werden. Analytics Platform System verfügt über zwei AD DS (Domänencontroller);  **_Appliance_domain_-AD01** und  **_Appliance_domain_-AD02**. Ändern Sie das DSRM-Kennwort mithilfe der folgenden Schritte für jeden Knoten Appliance AD.  
  
## <a name="HowToDSRM"></a>Das Administratorkennwort zurücksetzen  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster auf einem Knoten der Appliance AD ***Appliance_domain *-AD*Xx***virtuellen Computer.  
  
2.  Geben Sie an der Eingabeaufforderung `ntdsutil` ein.  
  
3.  Auf der **Ntdsutil** dazu aufgefordert werden, geben Sie `set dsrm password`.  
  
4.  Auf der **Administratorkennwort zurücksetzen:** dazu aufgefordert werden, geben Sie `reset password on server null`.  
  
5.  Geben Sie an der Eingabeaufforderung das neue Kennwort ein.  
  
6.  Wiederholen Sie die Schritte 1 bis 5 oben für jeden virtuellen Computer von AD-Anwendung.  
  
    > [!WARNING]  
    > Analytics Platform System unterstützt das Dollarzeichen ($) in der Administrator der Domäne oder lokaler Administratorkennwörter nicht. Ein Kennwort mit einem Dollarzeichen werden überprüft und werden verwendet, jedoch kann Upgrade- und wartungsplanlizenzen Aktivitäten blockieren.  
  
> [!NOTE]  
> Wenn auf dem virtuellen Computer oder die Active Directory Domain Services für eine bestimmte AD virtuelle Maschine beschädigt ist, ausgeführt **ReplaceVM** für die betroffenen AD virtuelle Computer die empfohlenen korrekturmaßnahmen ist. Wenden Sie sich an CSS, um Unterstützung zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
[Zurücksetzen des Kennworts &#40;Analytics Platform System&#41;](password-reset.md)  
  
