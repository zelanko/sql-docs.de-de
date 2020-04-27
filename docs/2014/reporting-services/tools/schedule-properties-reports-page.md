---
title: Zeitplaneigenschaften (Registerkarte Berichte) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 08fc68575e2515907f31e82cf3609d73da1c95d6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099786"
---
# <a name="schedule-properties-reports-page"></a>Zeitplaneigenschaften (Registerkarte Berichte)
  Verwenden Sie diese Seite, um eine Liste aller Berichte anzuzeigen, die diesen freigegebenen Zeitplan verwenden. Zeitpläne können zum Aktualisieren von Berichtsmomentaufnahmen, zum Generieren des Berichtsverlaufs, zum Auslösen eines Abonnements oder zum Kennzeichnen einer zwischengespeicherten Kopie des Berichts als abgelaufen verwendet werden. Wenn Sie herausfinden möchten, wie der Zeitplan verwendet wird, dann zeigen Sie die Eigenschaften- und Abonnementinformationen des Berichts an.  
  
 Zwar wird auf dieser Seite jeder Bericht angezeigt, der den freigegebenen Zeitplan verwendet, jedoch wird nicht angegeben, wie oft der freigegebene Zeitplan von einem einzelnen Bericht verwendet wird. Angenommen, 20 Abonnenten des Company Sales-Berichts verwenden alle den gleichen freigegebenen Zeitplan, um die Abonnementverarbeitung auszulösen. In diesem Fall wird der Company Sales-Bericht nur einmal in dieser Liste angezeigt, obwohl der Bericht 20 Verweise auf den freigegebenen Zeitplan besitzt.  
  
 Um diese Seite zu öffnen, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten Sie, stellen Sie eine Verbindung mit einem Berichts Server her, **Öffnen Sie den**Ordner frei **gegebene Zeitpläne** , klicken Sie mit der rechten Maustaste auf einen freigegebenen Zeitplan, und wählen Sie **Eigenschaften**aus.  
  
> [!NOTE]  
>  Diese Funktion ist nicht in jeder Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die von den-Editionen unterstützt werden, finden Sie [unter von den-Editionen unterstützte Funktionen SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473)).  
  
## <a name="options"></a>Optionen  
 **Ordner**  
 Gibt den Pfad des Berichts an.  
  
 **Bericht**  
 Gibt den Namen des Berichts an, der den Zeitplan verwendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen, Ändern oder Löschen von Zeitplänen](../subscriptions/create-modify-and-delete-schedules.md)   
 [Zeitpläne](../subscriptions/schedules.md)   
 [Berichts Server in Management Studio F1-Hilfe](report-server-in-management-studio-f1-help.md)   
 [Herstellen einer Verbindung mit einem Berichts Server in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Konfigurieren allgemeiner Eigenschaften für einen Bericht &#40;Berichts-Manager&#41;](../configure-general-properties-for-a-report-report-manager.md)  
  
  
