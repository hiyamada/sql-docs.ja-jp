---
title: LinRegIntercept (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a0c153182e1405ebedd26cc875c10068e280b654
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906242"
---
# <a name="linregintercept-mdx"></a>LinRegIntercept (MDX)


  セットの線形回帰を計算し、回帰直線では、x 切片の値を返します y ax+b の a を = です。  
  
## <a name="syntax"></a>構文  
  
```  
  
LinRegIntercept(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression_y*  
 有効な数値式です。通常は、Y 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Numeric_Expression_x*  
 有効な数値式です。通常は、X 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 最小ニ乗法による線型回帰では、回帰直線 (点の連続に最も適合する直線) の式を計算します。 回帰直線では次の式では、ここは傾き、b は切片は。  
  
 y = ax+b  
  
 **LinRegIntercept**関数は、y 軸の値を取得する最初の数値式に対して指定されたセットを評価します。 次に、2 番目の数値式が指定されている場合は、指定されているセットをその式に対して評価し、X 軸の値を取得します。 2 番目の数値式が指定されていない場合は、指定されたセット内のセルの現在のコンテキストを X 軸の値として使用します。 X 軸の引数を指定しない方法は、時間ディメンションでよく使用されます。   
  
 点のセットを取得した後、 **LinRegIntercept**関数は、回帰直線 (上記の式 b) の切片を返します。  
  
> [!NOTE]  
>  **LinRegIntercept**関数は空のセルまたはテキストや論理値を含むセルを無視します。 ただし、0 の値を持つセルは対象になります。  
  
## <a name="example"></a>例  
 次の例では、売上数量メジャーと店舗売上メジャーについて、回帰直線の切片を返しています。  
  
```  
LinRegIntercept(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
