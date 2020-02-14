---
title: Servereigenschaften (Seite „Sonstige Servereinstellungen“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.miscserversettings.f1
ms.assetid: b170c066-30cd-42dd-8d34-aa129ea09551
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62a8af2e4a82a0a0bdeec231db62c2166ed030de
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68030829"
---
# <a name="server-properties---misc-server-settings-page"></a>Servereigenschaften (Seite „Sonstige Servereinstellungen“)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Auf dieser Seite können Sie Ihre Servereinstellungen anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
 **Standardsprache für Benutzer**  
 Gibt die Standardsprache für alle neu erstellten Benutzernamen an.  
  
 **Zulassen, dass Trigger weitere Trigger auslösen**  
 Steuert, ob ein Trigger eine Aktion ausführen kann, die weitere Trigger auslöst. Wenn das Kontrollkästchen deaktiviert ist, können Trigger nicht von einem anderen Trigger ausgelöst werden. Wenn das Kontrollkästchen aktiviert ist, können Trigger über 32 Ebenen jeweils von einem anderen Trigger ausgelöst werden.  
  
 **Abfragekontrolle verwenden, um Abfragen mit langer Ausführungszeit zu verhindern**  
 Gibt eine zeitliche Obergrenze für die Ausführung einer Abfrage an. Die Abfragekosten beziehen sich auf eine geschätzte Zeit in Sekunden, die für das Ausführen einer Abfrage bei einer bestimmten Hardwarekonfiguration benötigt wird. Die Abfragekontrolle ist standardmäßig deaktiviert, und alle Abfragen können ausgeführt werden. Wenn diese Option ausgewählt ist, müssen Sie in das Textfeld unten ein Zeitlimit eingeben. Wenn Sie einen nicht negativen Wert ungleich null angeben, lässt die Abfragekontrolle die Ausführung von Abfragen, deren geschätzte Kosten über diesem Wert liegen, nicht zu.  
  
 **Zweistellige Jahresangaben als Jahre in diesem Bereich interpretieren**  
 Gibt den 100-Jahre-Datumsbereich zum Interpretieren von zweistelligen Jahreszahlenwerten an. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpretiert zweistellige Datumswerte so, dass auf das mit diesen Ziffern endende Jahr verwiesen wird, das in den angegebenen Bereich fällt.  
  
 Legen Sie im rechten Feld das Endjahr fest. Nach dem Speichern des Endjahres wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das linke Feld automatisch mit dem Startjahr aufgefüllt.  
  
 **Konfigurierte Werte**  
 Zeigt für die Optionen in diesem Bereich konfigurierte Werte an. Wenn Sie diese Werte ändern, klicken Sie anschließend auf **Ausgeführte Werte** , um zu sehen, ob die Änderungen wirksam sind. Wenn die Änderungen nicht wirksam geworden sind, muss die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zunächst neu gestartet werden.  
  
 **Ausgeführte Werte**  
 Zeigt die gegenwärtig ausgeführten Werte für die Optionen in diesem Bereich an. Diese Werte sind schreibgeschützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
