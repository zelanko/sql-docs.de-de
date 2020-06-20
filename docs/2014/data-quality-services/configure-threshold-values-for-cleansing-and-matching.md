---
title: Konfigurieren der Schwellenwerte für Bereinigung und Abgleich | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: eca69d431275229d1fb06c85c842f0257f7ef0e3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937961"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a>Konfigurieren der Schwellenwerte für Bereinigung und Abgleich
  In diesem Thema wird beschrieben, wie Schwellenwerte, die während den computerunterstützten Bereinigungs- und Abgleichsaktivitäten in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) verwendet werden, konfiguriert werden.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie müssen die Rolle „dqs_administrator“ in der DQS_MAIN-Datenbank haben, um diese Schwellenwerte zu konfigurieren.  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a> Konfigurieren der Schwellenwerte  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Konfiguration**.  
  
3.  Klicken Sie anschließend auf die Registerkarte **Allgemeine Einstellungen** . Auf dieser Registerkarte können Sie Schwellenwerte für die Bereinigung und abgleichsaktivitäten angeben.  
  
4.  Um Schwellenwerte für die Bereinigungsaktivität anzugeben, geben Sie entsprechende Werte in den folgenden Feldern im Bereich **Interaktive Bereinigung** an:  
  
    -   **Mindestergebnis für Vorschläge**: Das minimale Ergebnis oder der Vertrauensgrad, der von DQS zum Vorschlagen von Ersetzungen für einen Wert während des computerunterstützten Bereinigungsprozesses verwendet wird. Geben Sie einen Wert in der Dezimalnotation des entsprechenden Prozentwerts ein. Geben Sie beispielsweise 0,75 für 75 % ein. Dieser Wert sollte kleiner oder gleich dem Wert sein, der im Feld **Mindestergebnis für automatische Korrekturen** angegeben wurde. Der Standardwert ist 0,7.  
  
    -   **Mindestergebnis für automatische Korrekturen**: Das minimale Ergebnis oder der Vertrauensgrad, der von DQS zum automatischen Korrigieren eines Werts während des computerunterstützten Bereinigungsprozesses verwendet wird. Geben Sie einen Wert in der Dezimalnotation des entsprechenden Prozentwerts ein. Geben Sie beispielsweise 0,9 für 90 % ein. Der Standardwert ist 0,8.  
  
5.  Um einen Schwellenwert für die Abgleichsaktivität anzugeben, geben Sie einen Wert im Feld **Mindestergebnis für Datensätze** unter dem Bereich **Abgleich** an. Dieser Wert gibt das minimale Ergebnis für einen Datensatz an, das als Übereinstimmung mit einem anderen Datensatz betrachtet werden soll. Der Standardwert ist 80 %.  
  
6.  Klicken Sie auf **Schließen**.  
  
  
