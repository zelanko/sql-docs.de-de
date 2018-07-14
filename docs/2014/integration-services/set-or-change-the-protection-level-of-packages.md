---
title: Festlegen oder Ändern der Schutzebene von Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 94d29f4e488e68c5fda2549b793a26770480e30a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201650"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>Festlegen oder Ändern der Schutzebene von Paketen
  Wenn der Zugriff auf den Inhalt von Paketen und die darin enthaltenen vertraulichen Werte, z. B. Kennwörter, gesteuert werden soll, legen Sie den Wert der `ProtectionLevel`-Eigenschaft fest. Zum Erstellen des Projekts müssen die in einem Projekt enthaltenen Pakete die gleiche Schutzebene wie das Projekt aufweisen. Wenn Sie die `ProtectionLevel`-Eigenschafteneinstellung für das Projekt ändern, müssen Sie die Eigenschafteneinstellung für die Pakete manuell aktualisieren.  
  
 Informationen zum Ermitteln der `ProtectionLevel` Einstellungen, die in verschiedenen Phasen des Lebenszyklus der Paket für Ihre Pakete geeignet sind, finden Sie unter [Zugriffssteuerung für vertrauliche Daten in Paketen](security/access-control-for-sensitive-data-in-packages.md). Eine Übersicht über die Sicherheitsfeatures in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] finden Sie unter [Sicherheitsübersicht &#40;Integration Services&#41;](security/security-overview-integration-services.md).  
  
 Die Verfahren in diesem Thema wird beschrieben, wie die Verwendung [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] oder das Dtutil-eingabeaufforderungs-Hilfsprogramm so ändern Sie die `ProtectionLevel` Eigenschaft.  
  
> [!NOTE]  
>  Zusätzlich zu den Prozeduren in diesem Thema können Sie in der Regel festlegen oder Ändern der `ProtectionLevel` Eigenschaft eines Pakets, wenn Sie importieren oder exportieren das Paket. Sie können die `ProtectionLevel`-Eigenschaft eines Pakets auch ändern, wenn Sie ein Paket mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Import/Export-Assistenten speichern.  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>So legen Sie die Schutzebene eines Pakets in SQL Server-Datentools fest oder ändern sie  
  
1.  Überprüfen Sie die verfügbaren Werte für die `ProtectionLevel` Eigenschaft im Thema [Festlegen der Paketschutzebene](security/access-control-for-sensitive-data-in-packages.md), und bestimmen Sie den entsprechenden Wert für das Paket.  
  
2.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket.  
  
3.  Öffnen Sie das Paket im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer.  
  
4.  Wenn die Eigenschaften des Pakets nicht im Eigenschaftenfenster angezeigt werden, klicken Sie auf die Entwurfsoberfläche.  
  
5.  Im Fenster Eigenschaften in der **Sicherheit** gruppieren, wählen Sie den entsprechenden Wert für die `ProtectionLevel` Eigenschaft.  
  
     Wenn Sie eine Schutzebene auswählen, für die ein Kennwort erforderlich ist, geben Sie das Kennwort als Wert der **PackagePassword** -Eigenschaft an.  
  
6.  Wählen Sie im Menü **Datei** die Option **Ausgewählte Elemente speichern** aus, um das geänderte Paket zu speichern.  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>So legen Sie die Schutzebene von Paketen an der Eingabeaufforderung fest oder ändern sie  
  
1.  Überprüfen Sie die verfügbaren Werte für die `ProtectionLevel` Eigenschaft im Thema [Festlegen der Paketschutzebene](security/access-control-for-sensitive-data-in-packages.md), und bestimmen Sie den entsprechenden Wert für das Paket.  
  
2.  Überprüfen Sie die Zuordnungen für die `Encrypt` Option im Thema [Dtutil Utility](dtutil-utility.md), und ermitteln Sie die entsprechende ganze Zahl, die als Wert für den ausgewählten `ProtectionLevel` Eigenschaft.  
  
3.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
4.  Navigieren Sie zu dem Ordner mit der bzw. die Pakete, die für die Sie festlegen möchten, an der Eingabeaufforderung die `ProtectionLevel` Eigenschaft.  
  
     In den Syntaxbeispielen im folgenden Schritt wird davon ausgegangen, dass dieser Ordner der aktuelle Ordner ist.  
  
5.  Verwenden Sie zum Festlegen oder Ändern der Schutzebene für die Pakete einen Befehl wie in einem der folgenden Beispiele:  
  
    -   Der folgende Befehl legt die `ProtectionLevel` Eigenschaft eines einzelnen Pakets im Dateisystem auf Ebene 2, "Encrypt sensible Daten mit einem Kennwort", mit dem Kennwort "strongpassword festgelegt":  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   Mit dem folgenden Befehl wird die `ProtectionLevel`-Eigenschaft aller Pakete in einem bestimmten Ordner auf Ebene 2 ("Sensible Daten mit einem Kennwort verschlüsseln") mit dem Kennwort "strongpassword" festgelegt:  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Wenn Sie einen ähnlichen Befehl in einer Batchdatei verwenden, geben Sie den Dateiplatzhalter "%f" in der Batchdatei als "%%f" ein.  
  
## <a name="see-also"></a>Siehe auch  
 [dtutil (Hilfsprogramm)](dtutil-utility.md)  
  
  
