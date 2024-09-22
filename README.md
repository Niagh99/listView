```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using static System.Windows.Forms.VisualStyles.VisualStyleElement;

namespace listview
{
    public partial class Nghia : Form
    {
        public Nghia()
        {
            InitializeComponent();
        }

        private void btnAdd_Click(object sender, EventArgs e)
        {
            ListViewItem lvi = new ListViewItem(txtFirstName.Text);
            lvi.SubItems.Add(txtLastName.Text);
            lvi.SubItems.Add(txtPhone.Text);
            lvSinhVien.Items.Add(lvi);
        }

        private void btnDelete_Click(object sender, EventArgs e)
        {
            ListViewItem lvi = lvSinhVien.SelectedItems[0];

            lvi.SubItems[0].Text = txtFirstName.Text;
            lvi.SubItems[1].Text = txtLastName.Text;
            lvi.SubItems[2].Text = txtPhone.Text;
        }

        private void lvSinhVien_SelectedIndexChanged(object sender, EventArgs e)
        {
            if (lvSinhVien.SelectedItems.Count > 0)
            {
                ListViewItem lvi = lvSinhVien.SelectedItems[0];
                string fn = lvi.SubItems[0].Text;
                string ln = lvi.SubItems[1].Text;
                string phone = lvi.SubItems[2].Text;
                txtLastName.Text = ln;
                txtFirstName.Text = fn;
                txtPhone.Text = phone;
            }
        }

        private void binUpdate_Click(object sender, EventArgs e)
        {
            if (lvSinhVien.SelectedItems.Count > 0)

            {
                var selectedItem = lvSinhVien.SelectedItems[0];
                selectedItem.SubItems[0].Text = txtFirstName.Text;
                selectedItem.SubItems[1].Text = txtLastName.Text;
                selectedItem.SubItems[2].Text = txtPhone.Text;
                txtLastName.Clear();
                txtFirstName.Clear();
                txtPhone.Clear();
            }

            else
            {
                MessageBox.Show("Chon dong ban muon sua.");
            }
        }
    }
}
