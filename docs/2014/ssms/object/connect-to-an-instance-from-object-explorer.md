---
title: Verbinden mit einer Instanz mit dem Objekt-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 92e3b7b2099aabaa763fb6f6642bcc6267ebe6f1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63277433"
---
# <a name="connect-to-an-instance-from-object-explorer"></a>Verbinden mit einer Instanz mit dem Objekt-Explorer
  Um Objekte mittels Objekt-Explorer zu verwalten, müssen Sie zuerst den Objekt-Explorer mit der Instanz verbinden, die die Objekte enthält. Sie können den Objekt-Explorer gleichzeitig mit mehreren Instanzen verbinden.  
  
## <a name="connecting-object-explorer-to-a-server"></a>Herstellen einer Verbindung zwischen dem Objekt-Explorer und einem Server  
 Um den Objekt-Explorer verwenden zu können, müssen Sie zuerst eine Verbindung mit einem Server herstellen. Klicken Sie auf der Symbolleiste des Objekt-Explorers auf **Verbinden** , und wählen Sie in der Dropdownliste den Servertyp aus. Das Dialogfeld **Verbindung mit Server herstellen** wird geöffnet. Um eine Verbindung herzustellen, sind als Mindestangabe der Name des Servers und die richtigen Authentifizierungsinformationen erforderlich.  
  
## <a name="optional-object-explorer-connection-settings"></a>Optionale Verbindungseinstellungen für den Objekt-Explorer  
 Beim Herstellen einer Verbindung mit einem Server können Sie weitere Verbindungsinformationen im Dialogfeld **Verbindung mit Server herstellen** angeben. Im Dialogfeld **Verbindung mit Server herstellen** werden die zuletzt verwendeten Einstellungen beibehalten und von neuen Verbindungen wie z. B. neuen Fenstern des Code-Editors verwendet.  
  
 Zum Angeben optionaler Verbindungseinstellungen führen Sie die folgenden Schritte aus:  
  
1.  Klicken Sie auf der Symbolleiste des Objekt-Explorers auf **Verbinden** , und klicken Sie auf den Servertyp, mit dem eine Verbindung hergestellt werden soll. Das Dialogfeld **Mit Server verbinden** wird angezeigt.  
  
2.  Geben Sie in das Feld **Servername** den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz ein.  
  
3.  Klicken Sie auf **Optionen**. Im Dialogfeld **Verbindung mit Server herstellen** werden weitere Optionen angezeigt.  
  
4.  Klicken Sie auf die Registerkarte **Verbindungseigenschaften** , um die weiteren Einstellungen zu konfigurieren. Die verfügbaren Einstellungen variieren abhängig vom Servertyp. Die folgenden Einstellungen sind für [!INCLUDE[ssDE](../../includes/ssde-md.md)]verfügbar.  
  
    |Einstellung|BESCHREIBUNG|  
    |-------------|-----------------|  
    |**Verbindung mit Datenbank herstellen**|Treffen Sie eine Auswahl aus den verfügbaren Datenbanken auf dem Server. In dieser Liste werden nur Datenbanken angezeigt, für die Sie die Berechtigung zum Anzeigen haben.|  
    |**Netzwerkprotokoll**|Treffen Sie eine Auswahl aus Shared Memory, TCP/IP oder Named Pipes.|  
    |**Netzwerk Paketgröße**|Konfigurieren Sie in Byte. Die Standardeinstellung ist 4096 Byte.|  
    |**Verbindungs Timeout**|Konfigurieren Sie in Sekunden. Die Standardeinstellung ist 15 Sekunden.|  
    |**Ausführungstimeout**|Konfigurieren Sie in Sekunden. Die Standardeinstellung (0) weist darauf hin, dass es für die Ausführung kein Timeout gibt.|  
    |**Verbindung verschlüsseln**|Erzwingt die Verschlüsselung.|  
  
5.  Um den angegebenen Server zur Liste der registrierten Server hinzuzufügen, klicken Sie auf die Registerkarte **Registrierter Server** , klicken Sie auf den Speicherort für den neuen Server, und schließen Sie die Verbindung ab.  
  
> [!NOTE]  
>  Mithilfe der Seite **Zusätzliche Verbindungsparameter** können Sie der Verbindungszeichenfolge weitere Verbindungsparameter hinzufügen. Weitere Informationen finden Sie unter [Verbindung mit Server herstellen &#40;Seite „Zusätzliche Verbindungsparameter“&#41;](../../database-engine/connect-to-server-additional-connection-parameters-page.md).  
  
  
