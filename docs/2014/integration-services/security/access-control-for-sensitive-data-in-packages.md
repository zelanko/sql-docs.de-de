---
title: Zugriffssteuerung für sensible Daten in Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services], security
- protection levels for packages [Integration Services]
- configuration files [Integration Services]
- encryption [Integration Services]
- cryptography [Integration Services]
- security [Integration Services], protection levels
ms.assetid: d4b073c4-4238-41fc-a258-4e114216e185
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2d59a42fa7b77e6800218f1eeca4986320c1dcef
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62766777"
---
# <a name="access-control-for-sensitive-data-in-packages"></a>Zugriffssteuerung für vertrauliche Daten in Paketen
  Sie können die Daten in einem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket schützen, indem Sie eine Schutzebene festlegen, mit der nur vertrauliche Daten oder alle Daten im Paket geschützt werden. Darüber hinaus können Sie diese Daten mit einem Kennwort oder Benutzerschlüssel verschlüsseln oder die Daten von der Datenbank verschlüsseln lassen. Die für ein Paket verwendete Schutzebene ist außerdem nicht unbedingt statisch, sondern ändert sich im Lebenszyklus eines Pakets. Häufig wird eine Schutzebene während der Entwicklung und eine andere Schutzebene beim Bereitstellen des Pakets festgelegt.  
  
> [!NOTE]  
>  Zusätzlich zu den in diesem Thema beschriebenen Schutzebenen können Sie feste Rollen auf Datenbankebene verwenden, um Pakete zu schützen, die auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server gespeichert werden.  
  
## <a name="definition-of-sensitive-information"></a>Definition vertraulicher Informationen  
 In einem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket werden die folgenden Informationen als *vertraulich*definiert:  
  
-   Der Kennwortteil einer Verbindungszeichenfolge. Wenn Sie jedoch eine Option auswählen, mit der alle Daten verschlüsselt werden, wird die gesamte Verbindungszeichenfolge als vertraulich betrachtet.  
  
-   Die vom Task generierten XML-Knoten, die als sensibel markiert sind. Die Markierung der XML-Knoten wird von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] gesteuert und kann von den Benutzern nicht geändert werden.  
  
-   Alle Variablen, die als vertraulich markiert sind. Die Markierung der Variablen wird von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]gesteuert.  
  
 Ob [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] eine Eigenschaft als vertraulich einstuft oder nicht, hängt davon ab, ob der Entwickler der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Komponente, etwa ein Verbindungs-Manager oder Task, die Eigenschaft als vertraulich gekennzeichnet hat. Benutzer können Eigenschaften weder der Liste der als vertraulich eingestuften Eigenschaften hinzufügen, noch können sie sie aus dieser Liste entfernen.  
  
## <a name="encryption"></a>Verschlüsselung  
 Die Verschlüsselung, wie sie von Paketschutzebenen verwendet wird, wird mit der Datenschutz-API (DPAPI) von [!INCLUDE[msCoName](../../includes/msconame-md.md)] durchgeführt, die Teil der Kryptografie-API (CryptoAPI) ist.  
  
 Für die Paketschutzebenen, die Pakete mit Kennwörtern verschlüsseln, müssen Sie ebenfalls ein Kennwort angeben. Wenn Sie die Schutzebene von einer Ebene, die kein Kennwort verwendet, in eine Ebene ändern, die ein Kennwort verwendet, werden Sie zur Angabe eines Kennworts aufgefordert.  
  
 Für die Schutzebenen mit Kennwort wird in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] der Dreifach-DES-Verschlüsselungsalgorithmus mit einer Schlüssellänge von 192 Bits verwendet, der in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Bibliotheksklasse (FCL) verfügbar ist.  
  
## <a name="protection-levels"></a>Schutzebenen  
 In der folgenden Tabelle werden die in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verfügbaren Schutzebenen beschrieben. Die in Klammern stehenden Werte stammen aus der <xref:Microsoft.SqlServer.Dts.Runtime.DTSProtectionLevel> -Enumeration. Diese Werte werden im Eigenschaftenfenster angezeigt, das Sie zum Konfigurieren der Eigenschaften des Pakets verwenden, wenn Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]mit Paketen arbeiten.  
  
|Schutzebene|BESCHREIBUNG|  
|----------------------|-----------------|  
|Sensible Daten nicht speichern (`DontSaveSensitive`)|Unterdrückt die Werte vertraulicher Eigenschaften im Paket, wenn das Paket gespeichert wird. Diese Schutzebene verschlüsselt nicht, sondern verhindert stattdessen, dass als sensibel markierte Eigenschaften mit dem Paket gespeichert werden. Deshalb stehen die sensiblen Daten anderen Benutzern nicht zur Verfügung. Wenn das Paket von einem anderen Benutzer geöffnet wird, werden die sensiblen Daten durch Leerzeichen ersetzt und der Benutzer muss die sensiblen Daten angeben.<br /><br /> Bei der Verwendung mit dem **dtutil** -Hilfsprogramm (dtutil.exe) entspricht diese Schutzebene dem Wert 0.|  
|Alle Daten mit einem Kennwort verschlüsseln (`EncryptAllWithPassword`)|Verwendet ein Kennwort zum Verschlüsseln des gesamten Pakets. Das Paket wird mit einem Kennwort verschlüsselt, das beim Erstellen oder Exportieren des Pakets vom Benutzer bereitgestellt wird. Um das Paket im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu öffnen oder mit dem **dtexec** -Eingabeaufforderungs-Hilfsprogramm auszuführen, muss der Benutzer das Paketkennwort angeben. Ohne Kennwort kann der Benutzer das Paket weder öffnen noch ausführen.<br /><br /> Bei der Verwendung mit dem **dtutil** -Hilfsprogramm entspricht diese Schutzebene dem Wert 3.|  
|Alle Daten mit einem Benutzerschlüssel verschlüsseln (`EncryptAllWithUserKey`)|Verwendet einen auf dem aktuellen Benutzerprofil basierenden Schlüssel zum Verschlüsseln des gesamten Pakets. Nur der Benutzer, der das Paket erstellte oder exportierte, kann das Paket im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer öffnen oder mit dem Eingabeaufforderungs-Hilfsprogramm **dtexec** ausführen.<br /><br /> Bei der Verwendung mit dem **dtutil** -Hilfsprogramm entspricht diese Schutzebene dem Wert 4.<br /><br /> Hinweis: Für Schutzebenen, für die ein Benutzerschlüssel verwendet wird, werden in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DPAPI-Standards verwendet. Weitere Informationen zu DPAPI finden Sie in der MSDN Library unter [https://msdn.microsoft.com/library](https://go.microsoft.com/fwlink/?LinkId=15408).|  
|Sensible Daten mit einem Kennwort verschlüsseln (`EncryptSensitiveWithPassword`)|Verwendet ein Kennwort zum ausschließlichen Verschlüsseln der Werte vertraulicher Eigenschaften im Paket. Für diese Verschlüsselung wird DPAPI verwendet. Die sensiblen Daten werden als Teil des Pakets gespeichert, aber diese Daten werden mit einem Kennwort verschlüsselt, das vom aktuellen Benutzer beim Erstellen oder Exportieren des Pakets bereitgestellt wird. Um das Paket im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu öffnen, muss der Benutzer das Paketkennwort angeben. Falls kein Kennwort angegeben wird, wird das Paket ohne die sensiblen Daten geöffnet und der Benutzer muss neue Werte für sensible Daten angeben. Falls der Benutzer versucht, das Paket auszuführen, ohne das Kennwort anzugeben, schlägt die Paketausführung fehl. Weitere Informationen zu Kennwörtern und zur Befehlszeilenausführung finden Sie unter [dtexec (Hilfsprogramm)](../packages/dtexec-utility.md).<br /><br /> Bei der Verwendung mit dem **dtutil** -Hilfsprogramm entspricht diese Schutzebene dem Wert 2.|  
|Sensible Daten mit einem Benutzerschlüssel verschlüsseln (`EncryptSensitiveWithUserKey`)|Verwendet einen auf dem aktuellen Benutzerprofil basierenden Schlüssel zum ausschließlichen Verschlüsseln der Werte vertraulicher Eigenschaften im Paket. Das Paket kann nur von demselben Benutzer, der dasselbe Profil verwendet, geladen werden. Wenn das Paket von einem anderen Benutzer geöffnet wird, werden die sensiblen Daten durch Leerzeichen ersetzt und der aktuelle Benutzer muss neue Werte für die sensiblen Daten angeben. Wenn der Benutzer versucht, das Paket auszuführen, schlägt die Paketausführung fehl. Für diese Verschlüsselung wird DPAPI verwendet.<br /><br /> Bei der Verwendung mit dem **dtutil** -Hilfsprogramm entspricht diese Schutzebene dem Wert 1.<br /><br /> Hinweis: Für Schutzebenen, für die ein Benutzerschlüssel verwendet wird, werden in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DPAPI-Standards verwendet. Weitere Informationen zu DPAPI finden Sie in der MSDN Library unter [https://msdn.microsoft.com/library](https://go.microsoft.com/fwlink/?LinkId=15408).|  
|Serverspeicher für die Verschlüsselung verwenden (`ServerStorage`)|Schützt das gesamte Paket mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankrollen. Diese Option wird unterstützt, wenn ein Paket in der msdb-Datenbank von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert wird. Außerdem verwendet der SSISDB-Katalog die Schutzebene `ServerStorage`.<br /><br /> Diese Option wird nicht unterstützt, wenn ein Paket von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Dateisystem gespeichert wird.|  
  
## <a name="protection-level-setting-and-the-ssisdb-catalog"></a>Einstellung der Schutzebene und SSISDB-Katalog  
 Der SSISDB-Katalog verwendet die Schutzebene `ServerStorage`. Wenn Sie ein [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server bereitstellen, werden die Paketdaten und sensible Werte automatisch vom Katalog verschlüsselt. Die Daten werden vom Katalog auch automatisch entschlüsselt, wenn Sie sie abrufen.  
  
 Wenn Sie das Projekt (ISPAC-Datei) vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server in das Dateisystem exportieren, ändert das System die Schutzebene automatisch in `EncryptSensitiveWithUserKey`. Wenn Sie das Projekt mithilfe des Assistenten zum **Importieren von Projekt Integration Services** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]importieren, zeigt die **Schutzlevel** -Eigenschaft im Fenster **Eigenschaften** den Wert `EncryptSensitiveWithUserKey`an.  
  
## <a name="protection-level-setting-based-on-package-life-cycle"></a>Festlegen der Schutzebene auf Grundlage des Paketlebenszyklus  
 Die Schutzebene eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakets wird bei dessen Entwicklung in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] festgelegt. Wenn das Paket dann zu einem späteren Zeitpunkt bereitgestellt, von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]importiert oder daraus exportiert wird oder von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in den [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketspeicher oder in das Dateisystem kopiert wird, können Sie die Paketschutzebene aktualisieren. Wenn Sie z. B. Pakete auf Ihrem Computer mit einer Benutzerschlüssel-Schutzebenenoption erstellen und speichern, möchten Sie eventuell die Schutzebene ändern, wenn Sie das Paket anderen Benutzern übergeben; anderenfalls können diese Benutzer das Paket nicht öffnen.  
  
 Normalerweise wird die Schutzebene wie in den folgenden Schritten beschrieben geändert:  
  
1.  Behalten Sie während der Entwicklung den Standardwert für die Schutzebene der Pakete bei (`EncryptSensitiveWithUserKey`). Mit dieser Einstellung wird sichergestellt, dass nur der Entwickler vertrauliche Werte im Paket sehen kann. Sie können auch die Verwendung von `EncryptAllWithUserKey` oder `DontSaveSensitive` in Betracht ziehen.  
  
2.  Wenn Sie die Pakete bereitstellen möchten, müssen Sie die Schutzebene so ändern, dass sie nicht von dem Benutzerschlüssel des Entwicklers abhängig ist. Deshalb müssen Sie normalerweise `EncryptSensitiveWithPassword` oder `EncryptAllWithPassword` auswählen. Verschlüsseln Sie die Pakete, indem Sie ein temporäres sicheres Kennwort zuweisen, das auch dem Betriebsteam in der Produktionsumgebung bekannt ist.  
  
3.  Nach dem Bereitstellen der Pakete in der Produktionsumgebung kann das Betriebsteam die bereitgestellten Pakete erneut verschlüsseln, indem ein neues, nur dem Betriebsteam bekanntes sicheres Kennwort zugewiesen wird. Die bereitgestellten Pakete können auch verschlüsselt werden, indem `EncryptSensitiveWithUserKey` oder `EncryptAllWithUserKey` ausgewählt wird und die lokalen Anmeldeinformationen des Kontos verwendet werden, mit dem die Pakete ausgeführt werden.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Festlegen oder Ändern der Schutzebene von Paketen](../set-or-change-the-protection-level-of-packages.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Importieren und Exportieren von Paketen &#40;SSIS-Dienst&#41;](../import-and-export-packages-ssis-service.md)   
 [Integration Services &#40;SSIS-&#41; Paketen](../integration-services-ssis-packages.md)   
 [Sicherheitsübersicht &#40;Integration Services&#41;](security-overview-integration-services.md)  
  
  
