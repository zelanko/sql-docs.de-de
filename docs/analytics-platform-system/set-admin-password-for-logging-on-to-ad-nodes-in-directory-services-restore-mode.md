---
title: Active Directory Kennwort festlegen
description: Legen Sie Active Directory Knoten Administrator Anmelde Kennwort im Verzeichnisdienst-Wiederherstellungs Modus in Analytics Platform System (APS) fest.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6bbbf42106602a25b03072a9c9abfb04f04d3c49
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400333"
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>Festlegen des Administrator Kennworts für die Anmeldung bei AD-Knoten im Verzeichnisdienst-Wiederherstellungs Modus (DSRM)-Analytics Platform System
Der Verzeichnisdienst-Wiederherstellungs Modus (Directory Services Restore Mode, DSRM) ist ein Start Modus zum Reparieren oder Wiederherstellen Active Directory Domain Services (AD DS) Sie wird verwendet, um sich bei den AD-Knoten der Appliance anzumelden, nachdem AD DS fehlgeschlagen ist oder AD DS wieder hergestellt werden muss. Das Kennwort für DSRM wurde während der Einrichtung der Appliance am Hardwarehersteller Standort initialisiert und sollte vom Geräte Administrator geändert werden. Analytics Platform System verfügt über zwei AD DS (Domänen Controller); ** _appliance_domain_-ad01** und ** _appliance_domain_-ad02**. Ändern Sie das DSRM-Kennwort für jeden AD-Geräteknoten mithilfe der folgenden Schritte.  
  
## <a name="to-reset-the-administrator-password"></a><a name="HowToDSRM"></a>So setzen Sie das Administrator Kennwort zurück  
  
1.  Öffnen Sie ein Eingabe Aufforderungs Fenster auf einem AD-Knoten des Geräts <strong> _appliance_domain_AD_xx_</strong>virtuellen Computers.  
  
2.  Geben Sie an der Eingabeaufforderung `ntdsutil` ein:  
  
3.  Geben `set dsrm password`Sie an der Eingabeaufforderung von **Ntdsutil** ein.  
  
4.  Geben `reset password on server null`Sie an der Eingabeaufforderung **Administrator Kennwort zurücksetzen: ein** .  
  
5.  Geben Sie an der Eingabeaufforderung das neue Kennwort ein.  
  
6.  Wiederholen Sie die oben beschriebenen 1-5 Schritte für jeden virtuellen Geräte-AD-Computer.  
  
    > [!WARNING]  
    > Das Analytics Platform System unterstützt das Dollarzeichen ($) in den Domänen Administrator-oder lokalen Administrator Kennwörtern nicht. Ein Kennwort, das ein Dollarzeichen enthält, wird überprüft und ist verwendbar, kann aber upgradeaktivitäten und Wartungsaktivitäten blockieren.  
  
> [!NOTE]  
> Wenn die Active Directory Domain Services oder der virtuelle Computer für eine bestimmte virtuelle AD-Maschine beschädigt wird, wird das Ausführen von **replacevm** für die betroffene virtuelle AD-Maschine als Korrekturmaßnahme empfohlen. Wenden Sie sich an das CSS.  
  
## <a name="see-also"></a>Weitere Informationen  
[Kenn Wort Zurücksetzung &#40;Analytics-Platt Form System&#41;](password-reset.md)  
  
