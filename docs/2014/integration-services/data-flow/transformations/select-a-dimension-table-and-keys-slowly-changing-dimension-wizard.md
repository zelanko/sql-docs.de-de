---
title: Dimensionstabelle und Schlüssel auswählen (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f93d60b28488dbb910dcb727015c25848db220e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62770446"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Dimensionstabelle und Schlüssel auswählen (Assistent für langsam veränderliche Dimensionen)
  Mithilfe der Seite **Dimensionstabelle und Schlüssel auswählen** können Sie eine zu ladende Dimensionstabelle auswählen. Spalten aus dem Datenfluss werden den zu ladenden Spalten zugeordnet.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Optionen  
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
  
## <a name="see-also"></a>Siehe auch  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
