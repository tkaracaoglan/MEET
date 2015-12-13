// Choose City

using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForUser
{
    public partial class ChooseCity : System.Web.UI.Page
    {
       

        protected void Button1_Click(object sender, EventArgs e)
        {
          
        }

        protected void Button6_Click(object sender, EventArgs e)
        {
            
        }

        protected void Button7_Click(object sender, EventArgs e)
        {
            

        protected void Button10_Click(object sender, EventArgs e)
        {
        }

        protected void Button14_Click(object sender, EventArgs e)
        {
           
        }
        
        protected void Button16_Click(object sender, EventArgs e)
        {
           
        }

        protected void Button17_Click(object sender, EventArgs e)
        {
           
        }

        protected void Button22_Click(object sender, EventArgs e)
        {
           
        }

        protected void Button26_Click(object sender, EventArgs e)
        {
            
        }


        protected void Button34_Click(object sender, EventArgs e)
        {
           
        }

        protected void Button59_Click(object sender, EventArgs e)
        {
            
        }

        protected void Button61_Click(object sender, EventArgs e)
        {
        }

       

        

        
       

        

        

        
    }
}


// Login
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForUser
{
    public partial class Login : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {

        }
        
        protected void btnGirisYap_Click(object sender, EventArgs e)
        {
            
        }
    }
}


//Main Page
using System;
using System.Collections.Generic;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForUser
{
    public partial class MainPage : System.Web.UI.Page
    {
       

        protected void Page_Load(object sender, EventArgs e)
        {
          
        }

        protected void Button1_Click(object sender, EventArgs e)
        {
          
        }

        protected void rptUrunler_ItemCommand(object source, RepeaterCommandEventArgs e)
        {
           
        }

        private void SepetiGoster()
        {
            
        }

       
        protected void sepetonayla_Click(object sender, EventArgs e)
        {
          
        }

      

        
    }
}

//Order Page
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForUser
{
    public partial class OrderPage : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {

        }

        protected void Button1_Click(object sender, EventArgs e)
        {
           
        }
    }
}

//Register
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForUser
{
    public partial class Register : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {

        }
        
        protected void btnKayitOl_Click(object sender, EventArgs e)
        {
            
        }
    }
}


-tugba //Company Home Page
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Net.Mail;
using System.Web;
using System.Web.Services.Description;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForCompany
{
    public partial class CompanyHomePage : System.Web.UI.Page
    {
        MEETDBEntities2 db = new MEETDBEntities2();
        protected void Page_Load(object sender, EventArgs e)
        {
            if (IsPostBack) return;

            if (Session["Company"] != null)
            {
                Company company = (Company)Session["Company"];
                rptUrunler.DataSource = db.Products.Where(p => p.Category.CompID == company.CompID).ToList();
                rptUrunler.DataBind();
            }          
        }

        protected void btnGonder_Click(object sender, EventArgs e)
        {
            Uri baseUri = new Uri("http://localhost:7910/");
            Uri myUri = new Uri(baseUri, "CompanyPages/CompanyHomePage.aspx");
            Port prt = new Port();
            MailMessage ePosta = new MailMessage();
            ePosta.From = new MailAddress(txtEmail.Text);
            ePosta.To.Add("tugbakaracaoglan@hotmail.com");
            ePosta.Subject = txtKonu.Text;
            ePosta.Body = txtMesaj.Text;
            SmtpClient smtp = new SmtpClient();
            smtp.Credentials = new NetworkCredential("meetse301@gmail.com", "mehmetecemecetugba");
            smtp.Port = myUri.Port;
            smtp.Host = "mailin sunucu";
            smtp.Send(ePosta);
            btnGonder.Text = "eposta gönderildi";  
        }

        protected void btnTemizle_Click(object sender, EventArgs e)
        {
            txtKonu.Text = " ";
            txtMesaj.Text = " ";
            txtEmail.Text = " ";
        }
    }
}

//Company Login Page 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.CompanyPages
{
    public partial class CompanyLoginPage : System.Web.UI.Page
    {
        MEETDBEntities2 dbe = new MEETDBEntities2();
        protected void Page_Load(object sender, EventArgs e)
        {

        }

        protected void btnGiris_Click(object sender, EventArgs e)
        {
            MeetApplication.Company company = dbe.Companies.Where(c => c.CompEposta == txtEmailAdres.Text && c.CompPassword == txtSifre.Text).FirstOrDefault();
            if (company != null)
            {
                Session.Add("Company", company);
                Response.Redirect("/CompanyPages/CompanyHomePage.aspx");
            }
            else
            {
                Response.Redirect("/Errors/ErrorPage.aspx");
            }
        }
    }
}

//Admin Login
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForAdmin
{
    public partial class AdminLogin : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {

        }

        protected void btnGiris_Click(object sender, EventArgs e)
        {
            if (txtAdminAdi.Text == "Admin" && txtSifre.Text == "123")
            {
                Response.Redirect("/ForAdmin/HomePage.aspx");
            }
            else
            {
                Response.Redirect("Errors/404.aspx");
            }
        }
    }
}
Advertisement
sing System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForAdmin
{
    public partial class Advertisementt : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {

        }
        MEETDBEntities2 db = new MEETDBEntities2();
        protected void btnSil_Click(object sender, EventArgs e)
        {
            int id = Convert.ToInt32(txtSilAdvID.Text);
            Advertisement silinecekAdv = db.Advertisements.First(u => u.AdvID == id);
            db.Advertisements.Remove(silinecekAdv);
            db.SaveChanges();
        }

        protected void btnEkle_Click(object sender, EventArgs e)
        {
            Advertisement adv = new Advertisement();
            adv.CompName = txtCompName.Text;
            adv.HireDate = DateTime.Now;
            adv.Time = Convert.ToInt32(txtTime.Text);
            db.SaveChanges();
        }
    }
}

//Category
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForAdmin
{
    public partial class Categoryy : System.Web.UI.Page
    {
        MEETDBEntities2 db = new MEETDBEntities2();
        protected void Page_Load(object sender, EventArgs e)
        {

        }
        
        protected void btnEkle_Click(object sender, EventArgs e)
        {
            Category cat = new Category();
         
            cat.CompID = Convert.ToInt32(txtRestID.Text);
            cat.CatName = txtKatAdi.Text;

            db.Categories.Add(cat);
            db.SaveChanges();
        }

        protected void btnGuncelle_Click(object sender, EventArgs e)
        {
            int id = Convert.ToInt32(txtSilKatID.Text);
            Category silinecekCat = db.Categories.First(u => u.CatID == id);
            db.Categories.Remove(silinecekCat);
            db.SaveChanges();
        }

        protected void btnSil_Click(object sender, EventArgs e)
        {
            int id = Convert.ToInt32(txtGuncKatID.Text);
            Category guncellenecekCat = db.Categories.First(u => u.CatID == id);
            guncellenecekCat.CompID = Convert.ToInt32(txtGuncRestID.Text);
            guncellenecekCat.CatName = txtGuncKatAdi.Text;

            db.SaveChanges();
        }
    }
}
//Home Page
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace MeetApplication.ForAdmin
{
    public partial class Categoryy : System.Web.UI.Page
    {
        MEETDBEntities2 db = new MEETDBEntities2();
        protected void Page_Load(object sender, EventArgs e)
        {

        }
        
        protected void btnEkle_Click(object sender, EventArgs e)
        {
            Category cat = new Category();
         
            cat.CompID = Convert.ToInt32(txtRestID.Text);
            cat.CatName = txtKatAdi.Text;

            db.Categories.Add(cat);
            db.SaveChanges();
        }

        protected void btnGuncelle_Click(object sender, EventArgs e)
        {
            int id = Convert.ToInt32(txtSilKatID.Text);
            Category silinecekCat = db.Categories.First(u => u.CatID == id);
            db.Categories.Remove(silinecekCat);
            db.SaveChanges();
        }

        protected void btnSil_Click(object sender, EventArgs e)
        {
            int id = Convert.ToInt32(txtGuncKatID.Text);
            Category guncellenecekCat = db.Categories.First(u => u.CatID == id);
            guncellenecekCat.CompID = Convert.ToInt32(txtGuncRestID.Text);
            guncellenecekCat.CatName = txtGuncKatAdi.Text;

            db.SaveChanges();
        }
    }
}
