---
title: Debuggen eines Skripts durch Festlegen von Breakpoints in einem Skripttask und einer Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eec5d15ac6ff86bffeb93dc419cace76a066d59d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85426137"
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>Debuggen eines Skripts durch Festlegen von Breakpoints in einem Skripttask und einer Skriptkomponente
  In diesem Verfahren wird beschrieben, wie Sie in den Skripts Breakpoints festlegen, die im Skripttask und in der Skriptkomponente verwendet werden.  
  
 Nachdem Sie im Skript Breakpoints festgelegt haben, werden im Dialogfeld **Breakpoints festlegen- \<object name> ** die Breakpoints zusammen mit den integrierten Breakpoints aufgelistet.  
  
> [!IMPORTANT]  
>  In bestimmten Fällen werden Breakpoints im Skripttask und in der Skriptkomponente ignoriert. Weitere Informationen finden Sie im Abschnitt **Debuggen des Skript** Tasks in [Codieren und Debuggen des Skript](../control-flow/script-task.md) Tasks und im Abschnitt **Debuggen der Skript Komponente** unter [codieren und Debuggen der Skript Komponente] (.). /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.  
  
### <a name="to-set-a-breakpoint-in-script"></a>So legen Sie einen Breakpoint im Skript fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie auf das Paket mit dem Skript, in dem Sie Breakpoints festlegen möchten.  
  
3.  Um den Skripttask zu öffnen, klicken Sie auf die Registerkarte **Ablaufsteuerung**, und doppelklicken Sie dann auf den Skripttask.  
  
4.  Um die Skriptkomponente zu öffnen, klicken Sie auf die Registerkarte **Datenfluss**, und doppelklicken Sie dann auf die Skriptkomponente.  
  
5.  Klicken Sie auf **Skript** und dann auf **Skript bearbeiten**.  
  
6.  Suchen Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) die Skriptzeile, für die Sie einen Breakpoint festlegen möchten, klicken Sie mit der rechten Maustaste auf diese Zeile, zeigen Sie auf **Breakpoint**, und wählen Sie dann **Breakpoint einfügen** aus.  
  
     Das Breakpointsymbol wird in der Codezeile angezeigt.  
  
7.  Klicken Sie im Menü **Datei** auf **Beenden**.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
  
