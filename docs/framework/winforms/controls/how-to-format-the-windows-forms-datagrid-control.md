---
title: "如何：格式化 Windows Form DataGrid 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f03f65c878e72a8ec4b7f8bb447a1d6cf820690
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>如何：格式化 Windows Form DataGrid 控制項
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 將不同的色彩套用至各個部分<xref:System.Windows.Forms.DataGrid>控制項可以協助讓您更輕鬆地閱讀及解譯中的資訊。 色彩可以套用至資料列和資料行中。 資料列和資料行也可以隱藏或顯示自行斟酌。  
  
 有三個基本層面等的格式化<xref:System.Windows.Forms.DataGrid>控制項。 您可以設定屬性，以建立資料會顯示為預設樣式。 從該基底，您可以自訂某些資料表顯示在執行階段的方式。 最後，您可以修改哪些資料行中的資料格，以及色彩顯示，並顯示的其他格式設定。  
  
 格式化資料格在初始步驟，您可以設定的屬性<xref:System.Windows.Forms.DataGrid>本身。 這些色彩和格式的選擇會形成從中您可以再進行變更，取決於資料的資料表和顯示的資料行的基底。  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>若要建立之預設樣式的 DataGrid 控制項  
  
1.  視需要設定下列屬性：  
  
    |屬性|描述|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A>屬性定義的方格其偶數資料列的色彩。 當您將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>為不同的色彩屬性，每個資料列設定為這個新的色彩 （1、 3、 5 和等等的資料列）。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|方格其偶數資料列的背景色彩 （0、 2、 4、 6 和等等的資料列）。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|而<xref:System.Windows.Forms.DataGrid.BackColor%2A>和<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性決定在方格中，資料列的色彩<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>屬性決定 nonrow 區域中，才看得見，由上至下，捲動方格時，或者如果只有少數資料列中所包含的色彩在方格中。|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|方格的框線樣式，其中<xref:System.Windows.Forms.BorderStyle>列舉值。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|就會立即顯示方格上方的方格視窗標題的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|頂端的方格標題的字型。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|方格的視窗標題的背景色彩。|  
    |<xref:System.Windows.Forms.Control.Font%2A>|用來在方格中顯示文字的字型。|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|資料格的資料列中的資料顯示的字型色彩。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|資料格的格線色彩。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|分隔資料格方格，其中線條的樣式<xref:System.Windows.Forms.DataGridLineStyle>列舉值。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|資料列和資料行的標頭的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|資料行標頭所使用的字型。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|方格的資料行標頭，包括資料行標頭文字和加號/減號圖像 （glyph） （若要顯示多個相關的資料表時，請展開資料列） 的前景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|資料格，其中包含子資料表、 關聯性名稱和等等的連結中的所有連結的文字色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|在子資料表中，這會是父資料列的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|在子資料表中，這會是父資料列的前景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|判斷資料表和資料行名稱是否會顯示在父資料列，藉由<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列舉型別。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|方格中資料行的預設寬度 (單位為像素)。 重設之前設定此屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或是透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。<br /><br /> 屬性無法設為小於 0。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|在方格中的資料列的資料列高度 （以像素為單位）。 重設之前設定此屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或是透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。<br /><br /> 屬性無法設為小於 0。|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|方格的資料列行首的寬度。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|選取的資料列或資料格時，這是背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|選取的資料列或資料格時，這是前景色彩。|  
  
    > [!NOTE]
    >  請記住，當自訂控制項，便可將控制項設為無法存取，因為不佳的色彩選擇 （例如，紅色和綠色） 的色彩。 使用上可用的色彩**系統色彩**調色盤，若要避免這個問題。  
  
     下列程序假設您的表單具有<xref:System.Windows.Forms.DataGrid>控制項繫結至資料表。 如需詳細資訊，請參閱[繫結至資料來源的 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>以程式設計方式設定資料表的資料的資料表和資料行樣式  
  
1.  建立新的資料表樣式，並設定其屬性。  
  
2.  建立資料行樣式，並設定其屬性。  
  
3.  加入資料表樣式的資料行樣式集合中的資料行樣式。  
  
4.  將資料表樣式加入至資料格資料表樣式集合中。  
  
5.  在下列範例中，建立新的執行個體<xref:System.Windows.Forms.DataGridTableStyle>並設定其<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性。  
  
6.  建立的新執行個體**GridColumnStyle**並設定其**MappingName** （和其他配置和顯示屬性）。  
  
7.  針對您想要建立每個資料行樣式重複步驟 2 到 6。  
  
     下列範例說明如何<xref:System.Windows.Forms.DataGridTextBoxColumn>建立，因為資料行中顯示的名稱。 此外，您將資料行樣式<xref:System.Windows.Forms.GridColumnStylesCollection>的資料表樣式，並加入資料表樣式<xref:System.Windows.Forms.GridTableStylesCollection>資料格。  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
