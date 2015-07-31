#include <iostream>
#include <stdlib.h>
#include <time.h>

using namespace std;

int main()
{
	srand(time(NULL));

	int playerHP = 50;

	int attackDamage[3] = { 15, 25, 30 };
	int attackHitChance[3] = { 92, 50, 20 };

	int mudcrabHP = 30;

	int attackMDamage[3] = { 5, 10, 25 };
	int attackMHitChance[3] = { 100, 50, 10 };


	int entHP = 30;

	int attackEDamage[3] = { 5, 10, 20 };
	int attackEHitChance[3] = { 95, 75, 60 };

	int bossHP = 60;

	int attackBDamage[4] = { 30, 15, 40, 5 };
	int attackBHitChance[4] = { 50, 80, 35, 100 };



	int pathSelect = 1;

	cout << "You wake up in a forest in The Vale of Enduring Songs. Looking around, you see a note. The note instructs you to journey to The Mountain of the Vale. There is a creature to be found there. A beast known only by the name Terror. He has been killing the poor residents of Vale Town, in the shadow of the Mountain. You need to end his reign of terror! Pick your path to the Terror:  " << endl;
	cout << "1) Straight ahead, the forest thickens, with a trickle of sunlight reaching its way through the trees. Go this way?  " << endl;
	cout << "2) To your left the forest breaks, leading to gentle rolling hills. Go this way?  " << endl;
	cout << "3) The forest also breaks to your right, leading to a rocky seashore. Go towards the sea?  " << endl;

	cin >> pathSelect;
	if (pathSelect == 1)
	{
		cout << "Walking through the darkest parts of the forest, you begin to hear a rustling that suggest something a bit bigger than simple leaves in the wind. All of a sudden you see a tree that wasn't there before. Its eyes open and you prepare to fight what you realize is an Ent.  " << endl;
		while (true)
		{
			int playerChoice;
			int hitRoll = rand() % 100;

			cout << "Choose an attack with 1, 2, or 3 " << endl;
			cout << "1) Sword Slash " << endl;
			cout << "2) Lightning Hands " << endl;
			cout << "3) Magic Sphere " << endl;

			cin >> playerChoice;

			switch (playerChoice)
			{
			case 1:
				cout << "You slash at your enemy with your sword  " << endl;
				break;
			case 2:
				cout << "You shoot lightning at your enemy from your hands  " << endl;
				break;
			case 3:
				cout << "You shoot a sphere of magic towards your enemy which will explode on impact " << endl;
				break;
			}

			if (attackHitChance[playerChoice - 1] < hitRoll)
			{
				cout << "You hit him! " << endl;
				entHP -= attackDamage[playerChoice - 1];
				cout << "Ent's health is" << entHP << endl;
			}
			else
			{
				cout << "You missed! " << endl;
			}
			int entChoice = rand() % 3;
			hitRoll = rand() % 100;

			switch (entChoice)
			{
			case 0:
				cout << "The Ent roars at you! " << endl;
				break;
			case 1:
				cout << "The Ent grabs you with his roots and crushes you!  " << endl;
				break;
			case 2:
				cout << "The Ent wips you with his branch!  " << endl;
				break;
			}

			if (attackEHitChance[entChoice] < hitRoll)
			{
				cout << " He hits you!" << endl;
				playerHP -= attackEDamage[entChoice];
				cout << "Your health is" << playerHP << endl;
			}
			else
			{
				cout << "He misses" << endl;
			}

			if (playerHP < 1)
			{
				cout << "You are dead  " << endl;
				return 0;
			}
			if (entHP < 1)
			{
				cout << "You killed the Ent!  " << endl;
				break;
			}
		}
	}
	else if (pathSelect == 2)
	{
		cout << "Walking through the gentle hills, you recognize that the right choice has been made. None of the peaceful residents bother you. One kind farmer even gives you a Ruby Crystal to aid you in your quest. Your health raises by 15!  " << endl;
		playerHP = 75;


	}
	else if (pathSelect = 3)
	{
		cout << "The seashore is not as idyllic as its name suggests. The rocky landscape is unforgiving, and easily disguises the creatures lurking there. You walk straight a Giant Mudcrab, thankfully able to recover fast enough to engage.  " << endl;
		while (true)
		{
			int playerChoice;
			int hitRoll = rand() % 100;

			cout << "Choose an attack with 1, 2, or 3" << endl;
			cout << "1) Sword Slash" << endl;
			cout << "2) Lightning Hands" << endl;
			cout << "3) Magic Sphere" << endl;

			cin >> playerChoice;

			switch (playerChoice)
			{
			case 1:
				cout << "You slash at your enemy with your sword " << endl;
				break;
			case 2:
				cout << "You shoot lightning at your enemy from your hands " << endl;
				break;
			case 3:
				cout << "You shoot a sphere of magic towards your enemy which will explode on impact " << endl;
				break;

			default:
				cout << "You trip and skip your turn! " << endl;
			}

			if (attackHitChance[playerChoice - 1] < hitRoll)
			{
				cout << "You hit him!" << endl;
				mudcrabHP -= attackDamage[playerChoice - 1];
				cout << "Mudcrab's health is" << mudcrabHP << endl;
			}
			else
			{
				cout << "You missed!" << endl;
			}

			int mudcrabChoice = rand() % 3;
			hitRoll = rand() % 100;

			switch (mudcrabChoice)
			{
			case 0:
				cout << "The Giant Mudcrab attempts to bite you" << endl;
				break;
			case 1:
				cout << "The Giant Mudcrab tries to run into you" << endl;
				break;
			case 2:
				cout << "The Giant Mudcrab strikes you with his pincers" << endl;
				break;
			}

			if (attackHitChance[mudcrabChoice] < hitRoll)
			{
				cout << "The Mudcrab hit you!" << endl;
				playerHP -= attackDamage[mudcrabChoice];
				cout << "Your health is" << playerHP << endl;
			}
			else
			{
				cout << "He misses!" << endl;
			}
			if (playerHP < 1)
			{
				cout << "You are dead!" << endl;
				break;

			}
			if (mudcrabHP < 1)
			{
				cout << "You killed the Giant Mudcrab!" << endl;
				break;

			}
			

		}

	}
	int dialogueChoice;

	cout << "You enter Vale town, and head straight towards the Mayor to find out all that you can about The Terror. What do you ask the Mayor? Pick the corresponding number : " << endl;
	cout << "1) How large is the terror?" << endl;
	cout << "2) What is his strongest attack?" << endl;
	cout << "3) What is his weakness?" << endl;

	cin >> dialogueChoice;

		if (dialogueChoice == 1)
		{
			cout << "He is incredibly large. Some say as large as the mountain itself." << endl;
		}
		else if (dialogueChoice == 2)
		{
			cout << "The terror calls upon the element of fire, reigning down blazing boulders all around you." << endl;
		}
		else if (dialogueChoice == 3)
		{
			cout << "He is vulnerable to your attack 2; lightning hands." << endl;


			cout << "  You leave Vale Town and climb up the mountain. The skies get darker and darker the higher your climb. Eventually you reach the peak, and with that, The Terror. This beast is Fifty feet tall and seventy feet long with two large horns on its head, the most frightening creature you have ever seen." << endl;
			while (true)
			{
				int playerChoice;
				int hitRoll = rand() % 100;

				cout << "Choose an attack with 1, 2, or 3 " << endl;
				cout << "1) Sword Slash " << endl;
				cout << "2) Lightning Hands " << endl;
				cout << "3) Magic Sphere " << endl;

				cin >> playerChoice;

				switch (playerChoice)
				{
				case 1:
					cout << "You slash at your enemy with your sword  " << endl;
					break;
				case 2:
					cout << "You shoot lightning at your enemy from your hands  " << endl;
					break;
				case 3:
					cout << "You shoot a sphere of magic towards your enemy which will explode on impact " << endl;
					break;
				}

				if (attackHitChance[playerChoice - 1] < hitRoll)
				{
					cout << "You hit him! " << endl;
					bossHP -= attackDamage[playerChoice - 1];
					cout << "Boss's health is" << bossHP << endl;
				}
				else
				{
					cout << "You missed! " << endl;
				}
				int bossChoice = rand() % 4;
				hitRoll = rand() % 100;

				switch (bossChoice)
				{
				case 0:
					cout << "The Terror causes a massive earthquake. " << endl;
					break;
				case 1:
					cout << "The Terror charges at you full force.  " << endl;
					break;
				case 2:
					cout << "Flaming boulders fall from the sky.  " << endl;
					break;
				case 3:
					cout << "A mighty roar comes from The Terror." << endl;
				}

				if (attackBHitChance[bossChoice] < hitRoll)
				{
					cout << " He hits you!" << endl;
					playerHP -= attackBDamage[bossChoice];
					cout << "Your health is" << playerHP << endl;
				}
				else
				{
					cout << "He misses" << endl;
				}

				if (playerHP < 1)
				{
					cout << "You are dead  " << endl;
					break;
				}
				if (bossHP < 1)
				{
					cout << "You killed the Boss!  " << endl;
					break;
				}
				
			}
				
		}
		cout << "You saved the Vale! The Mayor names you Hero of the Vale. All is good, and you hang up your sword, and decided to live a peaceful life. Until you are needed again..." << endl;
	return 0;	
}
