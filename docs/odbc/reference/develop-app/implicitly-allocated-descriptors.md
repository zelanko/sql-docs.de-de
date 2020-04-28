---
title: Implizit zugeordnete Deskriptoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 271d479a9d2faa8cd7ab01e02e830b194c4138b2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300130"
---
# <a name="implicitly-allocated-descriptors"></a>Implizit zugewiesene Deskriptoren
Wenn ein Anweisungs Handle zugeordnet ist, ordnet die Anwendung implizit einen Satz von vier Deskriptoren zu. Die Anwendung kann die Handles dieser implizit zugeordneten Deskriptoren als Attribute des Anweisungs Handles abrufen. Wenn die Anwendung das Anweisungs Handle freigibt, gibt der Treiber alle implizit zugewiesenen Deskriptoren für dieses Handle frei.
