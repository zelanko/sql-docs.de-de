---
title: Dimensionstabelle und Schlüssel auswählen (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f0da6b425699a7bc99bb373b85fb65167e0864be
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35332344"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Dimensionstabelle und Schlüssel auswählen (Assistent für langsam veränderliche Dimensionen)
  Mithilfe der Seite **Dimensionstabelle und Schlüssel auswählen** können Sie eine zu ladende Dimensionstabelle auswählen. Spalten aus dem Datenfluss werden den zu ladenden Spalten zugeordnet.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Tastatur  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
