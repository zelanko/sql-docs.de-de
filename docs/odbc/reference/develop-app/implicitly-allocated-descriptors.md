---
title: Implizit zugeordnet Deskriptoren | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa25e99c5bc0b0a5799cfac479e97bd9b89db338
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447234"
---
# <a name="implicitly-allocated-descriptors"></a>Implizit zugewiesene Deskriptoren
Wenn ein Anweisungshandle zugeordnet ist, weist die Anwendung implizit einen Satz von vier Deskriptoren. Die Anwendung kann die Handles dieser implizit als Attribute des Anweisungshandles zugeordnet Deskriptoren erhalten. Wenn die Anwendung das Anweisungshandle frei, gibt der Treiber alle implizit zugewiesene Deskriptoren für dieses Handle frei.
