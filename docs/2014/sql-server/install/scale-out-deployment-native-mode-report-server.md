---
title: Horizontales Skalieren (Berichtsserver im einheitlichen Modus)-Bereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.scaleoutdeployment.F1
ms.assetid: 4df38294-6f9d-4b40-9f03-1f01c1f0700c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c091c115f9e03fbc0f1243e1c2fcf3a075f3586f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62753302"
---
# <a name="scale-out-deployment-native-mode-report-server"></a>Bereitstellung für horizontales Skalieren (Berichtsserver im einheitlichen Modus)
  Verwenden Sie die Seite **Bereitstellung für horizontales Skalieren** im Konfigurations-Manager für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , um den Initialisierungsstatus einer Bereitstellung für horizontales Skalieren anzuzeigen oder um einer Bereitstellung für horizontales Skalieren einen Berichtsserver hinzuzufügen. Eine *Bereitstellung für horizontales Skalieren* wird definiert als zwei oder mehr Berichtsserverinstanzen, die gemeinsam eine einzelne Berichtsserver-Datenbank nutzen.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus.  
  
 Ein *initialisierter Berichtsserver* beschreibt einen Server, der vertrauliche Daten ver- oder entschlüsseln kann, die in einer Berichtsserver-Datenbank gespeichert sind (gespeicherte Anmeldeinformationen und Verbindungszeichenfolgen sind Beispiele für verschlüsselte Daten, die in der Datenbank gespeichert sind). Die Berichtsserverinitialisierung ist eine Anforderung für Berichtsservervorgänge.  
  
 Eine *Bereitstellung für horizontales Skalieren* wird in den folgenden Szenarien verwendet:  
  
-   Als erforderliche Komponente für den Lastenausgleich mehrerer Berichtsserver in einem Servercluster. Bevor Sie einen Lastenausgleich für mehrere Berichtsserver ausführen können, müssen Sie sie zunächst für dieselbe Berichtsserver-Datenbank konfigurieren.  
  
-   Um Berichtsserver-Anwendungen auf verschiedenen Computern zu segmentieren, indem ein Server für die interaktive Berichtsverarbeitung und ein zweiter Server für die Planung der Berichtsverarbeitung verwendet wird. In diesem Szenario verarbeitet jede Serverinstanz verschiedene Anforderungen für denselben Berichtsserver-Inhalt, der in der freigegebenen Berichtsserver-Datenbank gespeichert ist.  
  
 Um eine Bereitstellung für horizontales Skalieren zu konfigurieren, beginnen Sie mit zwei oder mehr Berichtsserver-Instanzen, die alle mit derselben Berichtsserver-Datenbank verbunden sind. Nachdem alle Instanzen installiert sind, stellen Sie eine Verbindung zum ersten Berichtsserver her, und verwenden Sie anschließend die Seite Bereitstellung für horizontales Skalieren, um alle weiteren Instanzen zu verbinden. Nur ein Berichtsserver, der bereits für die Verwendung einer Datenbank initialisiert ist, kann zusätzliche Knoten initialisieren.  
  
 Um diese Seite zu öffnen, starten Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager, und klicken Sie im Navigationsbereich auf **Bereitstellung für horizontales Skalieren** . Weitere Informationen finden Sie unter [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Optionen  
 **SQL Server-Name**  
 Geben Sie den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz an, die die Berichtsserver-Datenbank hostet.  
  
 **Database Name**  
 Gibt den Namen der Datenbank an, mit der die Berichtsserverinstanz momentan verbunden ist.  
  
 **Servermodus**  
 Zeigt den Modus des Servers und der Datenbank an. Der Servermodus ist entweder systemeigen oder der integrierte SharePoint-Modus. Bereitstellungen für horizontales Skalieren werden für beide Modi unterstützt.  
  
 **Server**  
 Zeigt den Berichtsservernamen an. In den meisten Fällen ist dies der Name des Computers, auf dem der Berichtsserver installiert ist.  
  
 **Instanz**  
 Zeigt den Namen der Berichtsserverinstanz an. Berichtsserverinstanzen basieren auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen.  
  
 **Status**  
 Gibt an, ob der Berichtsserver initialisiert wird oder auf die Verknüpfung mit einer Bereitstellung für horizontales Skalieren wartet:  
  
-   Für einen eigenständigen Berichtsserver, der nicht Teil einer Bereitstellung für horizontales Skalieren ist, wird auf dieser Seite angezeigt, dass die Berichtsserverinstanz in Bezug auf die dedizierte Berichtsserver-Datenbank initialisiert wird. Der Status wird auf **Verknüpft**festgelegt.  
  
-   Für einen Berichtsserver, der auf die Verknüpfung mit einer Bereitstellung für horizontales Skalieren wartet, enthält diese Seite leere Werte für Server, Instanz und Status. Ein Berichtsserver wartet auf die Verknüpfung mit einer Bereitstellung für horizontales Skalieren, wenn Sie eine vorhandene Berichtsserver-Datenbank ausgewählt haben, die bereits von einer anderen Berichtsserverinstanz verwendet wird. Mit einer Meldung auf dieser Seite werden Sie angewiesen, eine Verbindung zu einem Berichtsserver herzustellen, der bereits mit der Serverfarm verknüpft ist. Um diese Anforderung abzuschließen, klicken Sie auf **Verbinden**, wählen Sie einen Berichtsserver, der bereits für die Berichtsserver-Datenbank initialisiert wurde. Klicken Sie dann auf **Bereitstellung für horizontales Skalieren**, wählen Sie die Berichtsserverinstanz mit dem Status **Es wird auf Verknüpfung gewartet**aus, und klicken Sie anschließend auf **Initialisieren**.  
  
-   Für einen Berichtsserver, der aktuell Teil einer Bereitstellung für horizontales Skalieren ist, wird auf dieser Seite der Initialisierungsstatus für alle Berichtsserverinstanzen angezeigt, die dieselbe Berichtsserver-Datenbank verwenden. Beim Anzeigen des Status einer Bereitstellung für horizontales Skalieren spielt es keine Rolle, mit welchem Server Sie verbunden sind. Die Statusinformationen werden für alle Knoten in der Bereitstellung für horizontales Skalieren auf gleiche Weise gemeldet.  
  
     Für einen Berichtsserver, der bereits Teil einer Bereitstellung für horizontales Skalieren ist, können Sie auf dieser Seite Knoten hinzufügen oder entfernen.  
  
 **Initialisieren**  
 Klicken Sie auf **Initialisieren** , um einen Berichtsserver zur Bereitstellung für horizontales Skalieren hinzuzufügen. Mit diesem Schritt wird ein Berichtsserver so konfiguriert, dass er einen symmetrischen Schlüssel in einer freigegebenen Berichtsserver-Datenbank verwendet. Mithilfe von **Initialisieren** können Sie einer Bereitstellung für horizontales Skalieren eine Berichtsserverinstanz hinzufügen oder ein Migrations- oder Installationsproblem beseitigen.  
  
 Eine Berichtsserverinstanz ist nur verfügbar, wenn zuvor eine Verbindung mit der freigegebenen Berichtsserverdatenbank konfiguriert wurde. Darüber hinaus müssen Sie die Initialisierung auf einem Berichtsserver ausführen, der bereits für die Verwendung der Berichtsserverdatenbank initialisiert ist.  
  
 **Entfernen**  
 Klicken Sie auf **Entfernen** , um die Verschlüsselungsschlüssel der ausgewählten Berichtsserverinstanz aus der Berichtsserverdatenbank auszuwählen. Sie können Schlüssel entfernen, um einen Berichtsserver aus einer Bereitstellung für horizontales Skalieren zu entfernen oder ein Migrations- oder Installationsproblem zu beseitigen. Mithilfe dieser Option werden nur die Verschlüsselungsschlüssel der angegeben Berichtsserverinstanz entfernt. Verschlüsselte Daten in der Berichtsserverdatenbank sind nicht betroffen.  
  
 Stellen Sie vorsichtshalber sicher, dass Sie eine Sicherungskopie des symmetrischen Schlüssels erstellen, bevor Sie ihn entfernen. Nachdem Sie die Verschlüsselungsschlüssel des letzten Berichtsservers in der Liste entfernt haben, führen Sie neue Anforderungen für sämtliche folgenden Berichtsserverinitialisierungen für die entsprechende Datenbank ein. Gemäß der neuen Anforderung müssen Sie, nachdem Sie einen Berichtsserver initialisiert haben, eine Sicherungskopie des symmetrischen Schlüssels erstellen. Das Wiederherstellen des symmetrischen Schlüssels ist notwendig, falls Sie auf die verschlüsselten Daten zugreifen möchten, die derzeit in der Berichtsserverdatenbank gespeichert sind.  
  
 Wenn Sie die verschlüsselten Daten nicht mehr benötigen oder falls Sie keine Sicherungskopie des Schlüssels besitzen, müssen Sie die verschlüsselten Daten löschen. Weitere Informationen finden Sie unter [Verschlüsselungsschlüssel &#40;einheitlicher SSRS-Modus&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Initialisieren eines Berichtsservers (SSRS-Konfigurations-Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)   
 [Konfigurieren eines Berichtsservers im einheitlichen Modus für Bereitstellungen für horizontales Skalieren &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  
