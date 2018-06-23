---
title: Dimensionstabelle und Schlüssel auswählen (Assistent für langsam veränderliche Dimensionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a62ab620db99e06f4e971e4bfe488f1741dd510
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160253"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Dimensionstabelle und Schlüssel auswählen (Assistent für langsam veränderliche Dimensionen)
  Mithilfe der Seite **Dimensionstabelle und Schlüssel auswählen** können Sie eine zu ladende Dimensionstabelle auswählen. Spalten aus dem Datenfluss werden den zu ladenden Spalten zugeordnet.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Konfiguration von Ausgaben mithilfe des Assistenten für langsam veränderliche Dimensionen](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  