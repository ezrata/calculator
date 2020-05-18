using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace HesapMakinesi
{
    public partial class HesapMakinesi : Form
    {
        double result = 0;
        bool optStatus = false;
        string opt = "";
        public HesapMakinesi()
        {
            InitializeComponent();
            textResult.Text = "0";
        }

        private void NumberEvent(object sender, EventArgs e)
        {
            if (textResult.Text == "0" || optStatus)
                textResult.Clear();

            optStatus = false;
                
            Button btn = (Button)sender;

            textResult.Text += btn.Text;
        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void optCalc(object sender, EventArgs e)
        {
            optStatus = true;
            Button btn = (Button)sender;
            string newOpt = btn.Text;

            lblResult.Text = lblResult.Text + " " + textResult.Text + " " + newOpt;
            switch (opt)
            {
                case "+": textResult.Text = (result + Double.Parse(textResult.Text)).ToString(); break;
                case "-": textResult.Text = (result - Double.Parse(textResult.Text)).ToString(); break;
                case "*": textResult.Text = (result * Double.Parse(textResult.Text)).ToString(); break;
                case "/": textResult.Text = (result / Double.Parse(textResult.Text)).ToString(); break;
                default:break;
            }

            result = Double.Parse(textResult.Text);
            textResult.Text = result.ToString();
            opt = newOpt;
        }

        private void Button4_Click(object sender, EventArgs e)
        {
            textResult.Text="0";
        }

        private void Button5_Click(object sender, EventArgs e)
        {
            textResult.Text = "0";
            lblResult.Text = "";
            opt = "";
            result = 0;
            optStatus = false;
        }

        private void Button9_Click(object sender, EventArgs e)
        {
            lblResult.Text = "";
            optStatus = true;

            switch (opt)
            {
                case "+": textResult.Text = (result + Double.Parse(textResult.Text)).ToString(); break;
                case "-": textResult.Text = (result - Double.Parse(textResult.Text)).ToString(); break;
                case "*": textResult.Text = (result * Double.Parse(textResult.Text)).ToString(); break;
                case "/": textResult.Text = (result / Double.Parse(textResult.Text)).ToString(); break;
                default: break;
            }


            result = Double.Parse(textResult.Text);
            textResult.Text = result.ToString();
            opt = "";
        }

    }
}
 
