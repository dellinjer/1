    public partial class LOGIN : Form
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
________________________________________________________________________________
{
    internal class DB
    {
        MySqlConnection connection = new MySqlConnection("server=localhost;port=3306;database=popa;uid=root;password=root");

        public void openConnection()
        {
            if (connection.State != System.Data.ConnectionState.Closed)
               connection.Open();
            
        }

        public void closeConnection()
        {
            if (connection.State != System.Data.ConnectionState.Open)
                connection.Close();
        }
        public MySqlConnection getConnection()
        {
            return connection;
        }
    }
}
________________________________________________________________________
{
    public partial class RegisterForm : Form
    {
        public RegisterForm()
        {
            InitializeComponent();
            userName.Text = "Введите имя";

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
    }
}
______________________________________________________________________________
заходим в вижл студио-> виндоус формс-> создаем проект и ставим виндоус ворм -> создался проект с пустым окном-> удаляем Forms1 которая находится с правой стороны.-> правой кнопкой мыши назымаем на весь проект и выбираем добавить -> форма виндоус -> даем имя новому окну->  уменьшаем окно ->открываем панель элементов-> panel-> устанавливаем панель сверху экрана и в свойствах в макете находим Dock и указываем на все окно в доке-> меняем цвет панели ( бэкграунд колор) или если картинку устанавливаем то указываем (бэкграунд имедж)-> опять ставим panel но только сверху-> дабавляем текстовый элемент label->перебравываем ее на верхнюю панель и открываем в свойствах Font и выставляем любой шрифт ( цвет меняется в ForeColor)-> переходим в макет предварительно выделяя лэйбл заходим в Dock и выставляем на всю шир и выс крч центр в доке.->текст меняется  в (внешнем виде) (текст) а в разработке нэйм это название самого элемента.-> в тексте пишим Авторизация-> в TextAlign поставить по центру-> а затем в AutoSize поставить фолз а не тру!!!-> создаем еще один Label это будет будущая кнопка-> меняем текст с название лэйбл 2 или что то типо того на (Х) крестик крч -> в ForeColor поменять цвет на белый -> меняем шрифт в size -> меняем курсор на hand ->в програмс надо вызвать не Forms1 а вписать название проекта по вызову окна авторизации.-> ДЛЯ ТОГО ЧТОБЫ ПОСТАВИТЬ КАРТИНКУ РЯДОМ С ПАРОЛЕМ И ЛОГИНОМ НУЖНО-> Выбираэв элемент под названием PictureBox(внутрь данной хуйни можно поместить картинку) -> задем нужно сделать папку с правой стороны в которой будут храниться картинки-> чтобы это сделать нужно нажать на весь проект -> добавить ->создать папку-> саму папку называем Images-> на сайте iconfinder скачиваем user и lock -> затем переносим карти нки в папку ->  выбрать картинку можно с помощьб Initiallmage в свойствах или какойто хрени рядом и затем импортируеш картинки из файл ресурс проекта.-> затем картинку нужно уменьшать или же увеличивать порпационально размеру данного квадрата-> заходим в свойства -> поведение -> SizeMode -> StretchImage-> затем заходим в свойства потом в макет и там будет Size и устанавливаем их 64х64.-> потом установим TextBox в панеле элементов ->ставим его на нашу 
