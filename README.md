# 1    public partial class LOGIN : Form
    {
        public LOGIN()
        {
            InitializeComponent();
            this.passworld.AutoSize = false;
            this.passworld.Size = new Size(this.passworld.Size.Width, 50);
        }

        private void closeButton_Click(object sender, EventArgs e)
        {
            this.Close();

        }

        private void closeButton_MouseEnter(object sender, EventArgs e)
        {
            closeButton.ForeColor = Color.Green;
        }

        private void closeButton_MouseLeave(object sender, EventArgs e)
        {
            closeButton.ForeColor = Color.Red;
        }
        Point lastPoint;
        private void panel1_MouseMove(object sender, MouseEventArgs e)
        {
            if (e.Button == MouseButtons.Left)
            {
                this.Left += e.X - lastPoint.X;
                this.Top += e.Y - lastPoint.Y;
            }
        }

        private void panel1_MouseDown(object sender, MouseEventArgs e)
        {
            lastPoint = new Point(e.X, e.Y);
        }

        Point thePoint;
        private void label1_MouseMove(object sender, MouseEventArgs e)
        {
            if (e.Button == MouseButtons.Left)
            {
                this.Left += e.X - thePoint.X;
                this.Top += e.Y - thePoint.Y;
            }

        }

        private void label1_MouseDown(object sender, MouseEventArgs e)
        {
            thePoint = new Point(e.X, e.Y);
        }

        private void buttonlogin_Click(object sender, EventArgs e)
        {
            String loginuser = loginField.Text;
            String passuser = passworld.Text;

            DB db = new DB();

            DataTable tabel = new DataTable();

            MySqlDataAdapter adapter = new MySqlDataAdapter();

            MySqlCommand command = new MySqlCommand("SELECT * FROM `users` WHERE `login` = @ul AND `pass` = @up", db.getConnection());

            command.Parameters.Add("@ul", MySqlDbType.VarChar).Value = loginuser;
            command.Parameters.Add("@up", MySqlDbType.VarChar).Value = passuser;

            adapter.SelectCommand = command; 
            adapter.Fill(tabel);

            if (tabel.Rows.Count > 0)
                MessageBox.Show("Yes");
            else
                MessageBox.Show("No");
        }
    }
}
