# css-practice
<div>
  <pre>
  [defult.aspx]
  <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="Practiceeasp._Default" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">

    <div style="padding:15px">
       
        <table class="nav-justified">
            <tr>
                <td colspan="2" style="font-size: x-large; font-weight: bold; color: #000000">Crud Operation</td>
            </tr>
            <tr>
                <td style="width: 401px">
                    <asp:Label ID="Label2"  runat="server" Font-Size="Medium" Text="Employee Id"></asp:Label>
                </td>
                <td>
                    <asp:TextBox ID="TextBox1"   runat="server" Font-Size="Medium" Width="200px"></asp:TextBox>
                </td>
            </tr>
            <tr>
                <td style="height: 20px; width: 401px">
                    <asp:Label ID="Label3" runat="server" Font-Size="Medium" Text="Employee Name"></asp:Label>
                </td>
                <td style="height: 20px">
                    <asp:TextBox ID="TextBox2" runat="server" Font-Size="Medium" Width="200px"></asp:TextBox>
                </td>
            </tr>
            <tr>
                <td style="width: 401px">
                    <asp:Label ID="Label4" runat="server" Font-Size="Medium" Text="Employee City"></asp:Label>
                </td>
                <td>
                    <asp:DropDownList ID="DropDownList1" runat="server" Font-Size="Medium" Width="200px">
                        <asp:ListItem Selected="True">New York</asp:ListItem>
                        <asp:ListItem>Chicago</asp:ListItem>
                        <asp:ListItem>Texas</asp:ListItem>
                        <asp:ListItem>Washington</asp:ListItem>
                    </asp:DropDownList>
                </td>
            </tr>
            <tr>
                <td style="width: 401px; height: 22px">
                    <asp:Label ID="Label5" runat="server" Font-Size="Medium" Text="Employee Sex"></asp:Label>
                </td>
                <td style="height: 22px">
                    <asp:RadioButtonList ID="RadioButtonList1" runat="server" RepeatDirection="Horizontal">
                        <asp:ListItem Selected="True">Male</asp:ListItem>
                        <asp:ListItem>Female</asp:ListItem>
                    </asp:RadioButtonList>
                </td>
            </tr>
            <tr>
                <td style="width: 401px">
                    <asp:Label ID="Label6" runat="server" Font-Size="Medium" Text="Employee Age"></asp:Label>
                </td>
                <td>
                    <asp:TextBox ID="TextBox3" runat="server" Font-Size="Medium" Width="200px"></asp:TextBox>
                </td>
            </tr>
            <tr>
                <td style="width: 401px">
                    <asp:Label ID="Label7" runat="server" Font-Size="Medium" Text="Joining Date"></asp:Label>
                </td>
                <td>
                    <asp:TextBox ID="TextBox4" runat="server" Font-Size="Medium" Width="200px"></asp:TextBox>
                </td>
            </tr>
            <tr>
                <td style="width: 401px">
                    <asp:Label ID="Label8" runat="server" Font-Size="Medium" Text="Contact"></asp:Label>
                </td>
                <td>
                    <asp:TextBox ID="TextBox5" runat="server" Font-Size="Medium" Width="200px"></asp:TextBox>
                </td>
            </tr>
              <tr>
                <td style="width: 401px">
                </td>
                <td>
                      <asp:Label ID="Label9" runat="server" Font-Size="Medium" Text=""></asp:Label>
                </td>
            </tr>
             <tr>
                <td style="width: 401px; height: 26px;">
                </td>
                <td style="height: 26px">
                    <asp:Button ID="Button1" runat="server" BackColor="Black" ForeColor="White" Text="Create" OnClick="Button1_Click" />
                    <asp:Button ID="Button2" runat="server" BackColor="Black" ForeColor="White" Text="Update" OnClick="Button2_Click" />
                    <asp:Button ID="Button3" runat="server" BackColor="Black" ForeColor="White" Text="Delete" OnClick="Button3_Click" />
                </td>
            </tr>

             <tr>
                <td colspan="2">
                    <asp:SqlDataSource ID="SqlDataSource1" runat="server"></asp:SqlDataSource>
                    <asp:GridView ID="GridView1" runat="server"  OnSelectedIndexChanged="GridView1_SelectedIndexChanged" AutoGenerateSelectButton = "True" Width="924px">
                    </asp:GridView>
                </td>
            </tr>
            
        </table>
       
    </div>

</asp:Content>
</pre>
</div>
