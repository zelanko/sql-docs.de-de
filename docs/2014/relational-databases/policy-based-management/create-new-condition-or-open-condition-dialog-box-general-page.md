---
title: Dialogfeld 'Neue Bedingung erstellen' oder 'Bedingung öffnen', Seite 'Allgemein' | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.condition.f1
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 296cdebc8a7a290cf8cdd848359ad776fa290c30
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52798292"
---
# <a name="create-new-condition-or-open-condition-dialog-box-general-page"></a>Dialogfeld 'Neue Bedingung erstellen' oder 'Bedingung öffnen', Seite 'Allgemein'
  Mithilfe dieses Dialogfelds können Sie eine richtlinienbasierte Verwaltungsbedingung erstellen oder ändern. Eine Bedingung ist ein boolescher Ausdruck, der einen Satz zulässiger Zustände eines durch die richtlinienbasierte Verwaltung verwalteten Ziels für Facets angibt. Die Eigenschaften, die im Feld **Ausdruck/Feld** ausgewählt werden können, hängen vom verwendeten Facet ab. Weitere Informationen darüber, wie Bedingungen mit Facets und Richtlinien zusammenhängen finden Sie unter [Verwalten von Servern mit der richtlinienbasierten Verwaltung](administer-servers-by-using-policy-based-management.md).  
  
## <a name="options"></a>Optionen  
 **Name**  
 Geben Sie für eine Bedingung den Namen der neuen Bedingung ein. Für eine vorhandene Bedingung wird der Name angezeigt.  
  
 **Facet**  
 Das von dieser Bedingung verwendete Facet.  
  
 **And/Or**  
 Wenn Sie mehrere Ausdrücke hinzufügen, wird hiermit angegeben, ob die Ausdrücke mit **Und** oder **Oder**verbunden werden sollen. Bleibt leer, wenn nur ein Ausdruck vorhanden ist.  
  
 **Feld**  
 Jedes Facet macht eine oder mehrere Eigenschaften verfügbar, die festgelegt werden können. Wählen Sie im Feld Feld eine Eigenschaft aus der Liste der verfügbaren Eigenschaften aus, um einen Ausdruck für diese Bedingung zu erstellen.  
  
 **Operator**  
 Wählen Sie einen Vergleichsoperator für diesen Ausdruck aus. Folgende Operatoren sind verfügbar: =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN. Für einige Eigenschaften sind nicht alle Operatoren verfügbar.  
  
 **Wert**  
 Die Werteinstellung für diesen Ausdruck. Die zulässigen Werte hängen vom Facet ab. Werte können WAHR/FALSCH, eine Zeichenfolge oder ein numerischer Wert sein. Zeichenfolgenwerte müssen in einfache Anführungszeichen ein, z. B. eingeschlossen werden: **'AdventureWorks'**. Für einige Eigenschaften sind nicht alle Operatoren verfügbar.  
  
## <a name="group-clauses"></a>Klauseln gruppieren  
 Klauseln können gruppiert werden, sodass sie vom Rest der Abfrage getrennt als einzelne Einheit ausgeführt werden. Dies ist mit Klammern um einen Ausdruck in einer mathematischen Gleichung oder einer Logikaussage vergleichbar. Das Gruppieren von Klauseln ist beim Erstellen von komplexen Abfragen hilfreich.  
  
 **So gruppieren Sie Klauseln**  
  
-   Drücken Sie UMSCHALT oder STRG, und klicken Sie dann auf zwei oder mehr Klauseln, um einen Bereich auszuwählen. Klicken Sie mit der rechten Maustaste auf den ausgewählten Bereich, und klicken Sie anschließend auf **Klauseln gruppieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](administer-servers-by-using-policy-based-management.md)  
  
  
