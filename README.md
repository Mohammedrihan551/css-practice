# css-practice
<div>
  <pre>
  [default.spx.cs]
   using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;
using System.Data.SqlClient;
using System.Data;

namespace Practiceeasp
{
    public partial class _Default : Page
    {

        SqlConnection connection = new SqlConnection("Data Source=LAPTOP-6MUQ531V;Initial Catalog=practice_db;Integrated Security=True");


        protected void Page_Load(object sender, EventArgs e)
        {
            if (!IsPostBack)
            {
                GetEmployeeList();
            }
        }



        protected void Button1_Click(object sender, EventArgs e)
        {
            try
            {
                string ename = Convert.ToString(TextBox2.Text);
                string ecity= Convert.ToString(DropDownList1.SelectedValue);
                string esex = Convert.ToString(RadioButtonList1.SelectedValue);
                float eage = float.Parse(TextBox3.Text);
                DateTime ejoining = DateTime.Parse(TextBox4.Text);
                string econtact =Convert.ToString(TextBox5.Text);

                connection.Open();


                SqlCommand command = new SqlCommand("Insert into employee  values (@name,@city,@age,@sex,@joining,@contact)",connection);
                command.Parameters.AddWithValue("@name",ename);
                command.Parameters.AddWithValue("@city", ecity);
                command.Parameters.AddWithValue("@age", eage);
                command.Parameters.AddWithValue("@sex", esex);
                command.Parameters.AddWithValue("@joining", ejoining);
                command.Parameters.AddWithValue("@contact", econtact);
                command.ExecuteNonQuery();
                connection.Close();

                Label9.Text = "Employee Created";
                GetEmployeeList();

            }
            catch (Exception ex)
            {
                Label9.Text = ex.Message;
            }
        }

        void GetEmployeeList()
        {
            SqlCommand command = new SqlCommand("Select * from employee", connection);
            SqlDataAdapter sda = new SqlDataAdapter(command);
            DataTable dt = new DataTable();
            sda.Fill(dt);
            GridView1.DataSource = dt;
            GridView1.DataBind();
        }

        protected void Button2_Click(object sender, EventArgs e)
        {
            try
            {
                int id = int.Parse(TextBox1.Text);
                string ename = Convert.ToString(TextBox2.Text);
                string ecity = Convert.ToString(DropDownList1.SelectedValue);
                string esex = Convert.ToString(RadioButtonList1.SelectedValue);
                float eage = float.Parse(TextBox3.Text);
                DateTime ejoining = DateTime.Parse(TextBox4.Text);
                string econtact = Convert.ToString(TextBox5.Text);

                connection.Open();


                SqlCommand command = new SqlCommand("update employee  set name=@name,city=@city,age=@age,sex=@sex,joining=@joining,contact=@contact where id=@id ", connection);
                command.Parameters.AddWithValue("@id", id);
                command.Parameters.AddWithValue("@name", ename);
                command.Parameters.AddWithValue("@city", ecity);
                command.Parameters.AddWithValue("@age", eage);
                command.Parameters.AddWithValue("@sex", esex);
                command.Parameters.AddWithValue("@joining", ejoining);
                command.Parameters.AddWithValue("@contact", econtact);
                command.ExecuteNonQuery();
                connection.Close();

                Label9.Text = "Employee Updated";
                GetEmployeeList();

            }
            catch (Exception ex)
            {
                Label9.Text = ex.Message;
            }
        }

        protected void Button3_Click(object sender, EventArgs e)
        {
            try
            {
                int id = int.Parse(TextBox1.Text);
                connection.Open();

                SqlCommand command = new SqlCommand("delete employee  where id=@id ", connection);
                command.Parameters.AddWithValue("@id", id);
                command.ExecuteNonQuery();
                connection.Close();

                Label9.Text = "Employee Deleted";
                GetEmployeeList();

            }
            catch (Exception ex)
            {
                Label9.Text = ex.Message;
            }
        }

        protected void GridView1_SelectedIndexChanged(object sender, EventArgs e)
        {
            GridViewRow row = GridView1.SelectedRow;
            Label9.Text = row.Cells[2].Text;
            Response.Redirect("/new.aspx?id="+ row.Cells[1].Text+"&name="+ row.Cells[2].Text);
        }
    }
}


  
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
