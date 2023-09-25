using System;
using System.Drawing;
using System.Windows.Forms;

namespace coloresRandom
{
    public partial class frmSensorColores : Form
    {
        Random coloresAleatorios = new Random();
        public frmSensorColores()
        {
            InitializeComponent();
        }
        private void timerMuestra_Tick(object sender, EventArgs e)
        {
            // Usamos la función Color.FromArgb(R, G, B), estamos variando el color rojo
            IbISensorA.BackColor = Color.FromArgb(coloresAleatorios.Next(256), 0, 0);
            IbISensorB.BackColor = Color.FromArgb(coloresAleatorios.Next(256), 0, 0);
            IbISensorA.Text = "Sensor A: " + IbISensorA.BackColor.ToString();
            IbISensorB.Text = "Sensor B: " + IbISensorB.BackColor.ToString();

            if (IbISensorA.BackColor == IbISensorB.BackColor)
            {
                timerMuestra.Enabled = false; // Desactiva el timer
                MessageBox.Show("Coinciden los colores");
            }
        }
    }
}
