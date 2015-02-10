//# InformatikProjectSemester2
//Project for IT Class. Contributers: Moritz W., Sophie E.
using System;

namespace RPGKampfsystemConsoleEntwurf
{
	class Program
	{
		public static void Main(string[] args)
		{
			
			//INSERT COOSE_WEAPON CODE HERE!
			
			//Variablen für die Lebenspunkte des Spielers und Gegners initialisieren:
			double dLPgegner = 100;
			double dLPspieler = 100;
			//Variable für den Schaden:
			double dSchaden = 0;
			//Zufallsgenerator initialisieren:
			Random rGenerator = new Random();

			Console.WriteLine("Es kommt zu einem Kampf. Dein Gegner zieht seine Waffe zuerst.");
			//Schleife für den Kampf:
			while ( (dLPgegner > 0) && (dLPspieler > 0) )
			{
				dSchaden = rGenerator.Next(0, 11);
				Console.WriteLine("Dein Gegner schlägt zu. Du nimmst " + dSchaden + " Schaden.");
				if (dSchaden == 0)
				{
					Console.WriteLine("Dein Gegner hat dich verfehlt.");
				}
				if (dSchaden == 10)
				{
					Console.WriteLine("Dein Gegner hat dich hart getroffen");
				}

				dLPspieler = dLPspieler - dSchaden;
				Console.WriteLine("Du hast noch " + dLPspieler + " Lebenspunkte.");
				Console.ReadLine();


				if (dLPspieler >= 0)
				{
					dSchaden = rGenerator.Next (0, 11);
					Console.WriteLine ("Jetzt attackierst du deinen Gegner. Er nimmt " + dSchaden + " Schaden.");
					if (dSchaden == 0) {
						Console.WriteLine ("Du hast deinen Gegner verfehlt.");
					}
					if (dSchaden == 10) {
						Console.WriteLine ("Volltreffer!");
					}
					dLPgegner = dLPgegner - dSchaden;
					Console.WriteLine ("Dein Gegner hat noch " + dLPgegner + " Lebenspunkte.");
					Console.ReadLine ();
				}
			}

			if (dLPspieler <= 0)
			{
				Console.WriteLine("Du hast den Kampf verloren, denn du hast keine Lebenspunkte mehr übrig.");
				Console.WriteLine("Du bist endgültig tot und dein Gegner zieht siegreich hinfort.");
				Console.WriteLine("Dein Name wird zukünftig nur noch in alten Geschichtsbüchern auftauchen.");
			}
			if (dLPgegner <= 0)
			{
				Console.WriteLine("Du hast den Kampf gewonnen, dein Gegner hat keine Lebenspunkte mehr übrig.");
				Console.WriteLine("Er ist tot und du findest bei ihm einen Heiltrank, der deine Gesundheit wieder voll herstellt.");
				dLPspieler = 100;
			}
			Console.ReadLine ();
			Environment.Exit (0);

		}
	}
}
