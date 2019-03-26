---
title: Dimensionstabelle und Schlüssel auswählen (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f15e90d05b99bea9e774835a945d0061701a8050
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58276819"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Dimensionstabelle und Schlüssel auswählen (Assistent für langsam veränderliche Dimensionen)
  Mithilfe der Seite **Dimensionstabelle und Schlüssel auswählen** können Sie eine zu ladende Dimensionstabelle auswählen. Spalten aus dem Datenfluss werden den zu ladenden Spalten zugeordnet.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>enthalten  
 **Connection manager**  
 Wählen Sie in der Liste einen vorhandenen OLE DB-Verbindungs-Manager aus, oder erstellen Sie einen neuen OLE DB-Verbindungs-Manager, indem Sie auf **Neu** klicken.  
  
> [!NOTE]  
>  Der Assistent für langsam veränderliche Dimensionen unterstützt nur OLE DB-Verbindungs-Manager und Verbindungen mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Neu**  
 Verwenden Sie das Dialogfeld **OLE DB-Verbindungs-Manager konfigurieren** , um einen vorhandenen Verbindungs-Manager auszuwählen, oder klicken Sie auf **Neu** , um eine neue OLE DB-Verbindung herzustellen.  
  
 **Tabelle oder Sicht**  
 Wählen Sie eine Tabelle oder eine Sicht aus der Liste aus.  
  
 **Eingabespalten**  
 Wählen Sie aus der Liste der Eingabespalten aus, für die Sie Zuordnungen angeben können.  
  
 **Dimensionsspalten**  
 Zeigen Sie alle verfügbaren Dimensionsspalten an.  
  
 **Schlüsseltyp**  
 Wählen Sie eine der Dimensionsspalten aus, die als Geschäftsschlüssel verwendet werden soll. Sie müssen über einen Geschäftsschlüssel verfügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
