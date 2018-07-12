---
title: Erstellen einer Multiserverumgebung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, multiserver environments
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- multiserver environments [SQL Server]
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
caps.latest.revision: 41
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8cecfa64f8aa6656cf055a9e488cfe30d68d5160
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183597"
---
# <a name="create-a-multiserver-environment"></a>Erstellen einer Multiserverumgebung
  Die Multiserververwaltung erfordert, dass Sie einen Masterserver (MSX) und einen oder mehrere Zielserver (TSX) einrichten. Aufträge, die auf allen Zielservern verarbeitet werden, müssen zuerst auf dem Masterserver definiert werden, und dann zu den Zielservern heruntergeladen werden.  
  
 Standardmäßig sind die vollständige SSL-Verschlüsselung (Secure Sockets Layer) und die Zertifikatüberprüfung für Verbindungen zwischen Masterservern und Zielservern aktiviert. Weitere Informationen finden Sie unter [Festlegen von Verschlüsselungsoptionen auf Zielservern](set-encryption-options-on-target-servers.md).  
  
 Wenn Sie eine große Anzahl von Zielservern haben, vermeiden Sie, den Masterserver auf einem Produktionsserver zu definieren, der bedeutende Leistungsanforderungen bezüglich anderer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionalität hat, da der Zielserverdatenverkehr die Leistung auf dem Produktionsserver verlangsamen kann. Wenn Sie auch Ereignisse an einen dedizierten Masterserver weiterleiten, können Sie die Administration auf einem Server zentralisieren. Weitere Informationen finden Sie unter [Verwalten von Ereignissen](manage-events.md).  
  
> [!NOTE]  
>  Um die Multiserver-Auftragsverarbeitung verwenden zu können, muss das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstkonto Mitglied der **msdb** -Datenbankrolle **TargetServersRole** auf dem Masterserver sein. Der Masterserver-Assistent fügt dieser Rolle im Rahmen des Eintragungsprozesses automatisch das Dienstkonto hinzu.  
  
## <a name="considerations-for-multiserver-environments"></a>Überlegungen zu Multiserverumgebungen  
 Details zu den unterstützten MSX-/TSX-Konfigurationen finden Sie in der folgenden Tabelle.  
  
||**TSX = 7.0**|**TSX = 8.0 &LT; SP3**|**TSX = 8.0 SP3 oder höher**|**TSX = 9.0**|**TSX = 10.0**|**TSX = 10,5**|**TSX = 11.0**|  
|-|--------------------|---------------------------|----------------------------------|--------------------|--------------------|---------------------|---------------------|  
|**MSX = 7.0**|ja|ja|nein|nein|nein|nein|nein|  
|**MSX = 8.0 &LT; SP3**|ja|ja|nein|nein|nein|nein|nein|  
|**MSX = 8.0 SP3 oder höher**|nein|nein|ja|ja|ja|ja|ja|  
|**MSX = 9.0**|nein|nein|nein|ja|ja|ja|ja|  
|**MSX = 10.0**|nein|nein|nein|nein|ja|ja|ja|  
|**MSX = 10,5**|nein|nein|nein|nein|nein|ja|ja|  
|**MSX = 11.0**|nein|nein|nein|nein|nein|nein|ja|  
  
 Beachten Sie die folgenden Punkte, wenn Sie eine Multiserverumgebung erstellen:  
  
-   Jeder Zielserver berichtet nur einem Masterserver. Sie müssen einen Zielserver aus einem Masterserver austragen, bevor Sie ihn bei einem anderen Masterserver eintragen können.  
  
-   Wenn Sie den Namen eines Zielservers ändern, müssen Sie ihn vor der Namensänderung austragen und danach wieder eintragen.  
  
-   Wenn Sie eine Multiserverkonfiguration auflösen möchten, müssen Sie alle Zielserver aus dem Masterserver austragen.  
  
-   SQL Server Integration Services unterstützt nur Zielserver, die über dieselbe Version wie der Masterserver oder eine höhere Version verfügen.  
  
## <a name="related-tasks"></a>Related Tasks  
 In den folgenden Themen werden allgemeine Aufgaben zum Erstellen einer Multiserverumgebung beschrieben.  
  
|Description|Thema|  
|-----------------|-----------|  
|Beschreibt, wie ein Masterserver erstellt wird.|[Einrichten eines Masterservers](make-a-master-server.md)|  
|Beschreibt, wie ein Zielserver erstellt wird.|[Erstellen eines Zielservers](make-a-target-server.md)|  
|Beschreibt, wie ein Zielserver bei einem Masterserver eingetragen wird.|[Eintragen eines Zielservers bei einem Masterserver](enlist-a-target-server-to-a-master-server.md)|  
|Beschreibt, wie der Austritt eines Zielservers aus einem Masterserver vollzogen wird.|[Vollziehen des Austritts eines Zielservers aus einem Masterserver](defect-a-target-server-from-a-master-server.md)|  
|Beschreibt, wie der Austritt mehrerer Zielserver aus einem Masterserver vollzogen wird.|[Vollziehen des Austritts mehrerer Zielserver aus einem Masterserver](defect-multiple-target-servers-from-a-master-server.md)|  
|Beschreibt, wie der Status eines Zielservers überprüft wird.|[Sp_help_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)<br /><br /> [Sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql)|  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung von proxybasierten Multiserveraufträgen](troubleshoot-multiserver-jobs-that-use-proxies.md)  
  
  
