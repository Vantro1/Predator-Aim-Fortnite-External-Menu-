# Predator-Aim-Fortnite-External-Menu-
Pasted Fortnite Cheat that Sinclear#0654 is trying to sell ( Skidded menu ) Original made by pІu#9024


namespace ZeroGui
{
	namespace Input
	{
		static bool mouseDown[5];
		static bool mouseDownAlready[256];

		static bool is_mouse_clicked(int button, int element_id, bool repeat)
		{
			if (mouseDown[button])
			{
				if (!mouseDownAlready[element_id])
				{
					mouseDownAlready[element_id] = true;
					return true;
				}
				if (repeat)
					return true;
			}
			else
			{
				mouseDownAlready[element_id] = false;
			}
			return false;
		}
	}





auto menu()->VOID {
	static ImVec2 pos(180, 100);
	if (ZeroGui::begin_window(0, pos, ImVec2(585.0f, 425.0f), MenuIsOpen, true))
	{
		ZeroGui::draw_filled_rect(ImVec2(pos.x - 2, pos.y - 2), 589.0f, 429.0f, ZeroGui::MenuColors::Window_Header);

		ZeroGui::draw_filled_rect(ImVec2(pos.x, pos.y), 585.0f, 425.0f, ZeroGui::MenuColors::Window_Background);
		ZeroGui::draw_filled_rect(ImVec2(pos.x, pos.y), 585.0f, 25.0f, ZeroGui::MenuColors::Window_Header);

		ImVec2 titlePos = ImVec2(pos.x + 585.0f / 2, pos.y + 25 / 2);
		ZeroGui::text_center(_("Predator Fortnite (Skidded Cheat and this menu was original made by pІu#9024"), titlePos, IM_COL32(255, 255, 255, 255));
		ZeroGui::text_normal(_(""));

		ZeroGui::next_column(30.0f);
		if (ZeroGui::button_tab(_("Main"), ImVec2(110, 25), tab == 1)) tab = 1;

		ZeroGui::next_column(165.0f);
		if (ZeroGui::button_tab(_("Visuals"), ImVec2(110, 25), tab == 2)) tab = 2;

		ZeroGui::next_column(300.0f);
		if (ZeroGui::button_tab(_("Exploits"), ImVec2(110, 25), tab == 3)) tab = 3;

		ZeroGui::next_column(435.0f);
		if (ZeroGui::button_tab(_("Miscellaneous"), ImVec2(110, 25), tab == 4)) tab = 4;

		if (tab == 1)
		{
			ZeroGui::next_column(30.0f);
			ZeroGui::text_normal(_(" "));

			ZeroGui::check_box(_("Aimbot"), &Settings::Aimbot);

			ZeroGui::zero_slider(_("Fov Circle"), &Settings::AimbotFOV, 1.0f, 500.0f);
			ZeroGui::zero_slider(_("Smoothness"), &Settings::AimbotSmooth, 1.0f, 10.0f);
		}

		if (tab == 2)
		{
			ZeroGui::next_column(30.0f);
			ZeroGui::text_normal(_(" "));

			ZeroGui::check_box(_("Bounded box"), &Settings::PlayerBox);
			ZeroGui::check_box(_("3D Box"), &Settings::Box3d);
			ZeroGui::check_box(_("Skeleton"), &Settings::Skeleton);
			ZeroGui::check_box(_("Username"), &Settings::PlayerName);
			ZeroGui::check_box(_("Snaplines"), &Settings::Snaplines);
			ZeroGui::check_box(_("Health"), &Settings::PlayerHealth);
			ZeroGui::check_box(_("Chams (glow)"), &Settings::Glow);
		}

		if (tab == 3)
		{
			ZeroGui::next_column(30.0f);
			ZeroGui::text_normal(_(" "));
			ZeroGui::check_box(_("Fast Skydive"), &Settings::SkydiveSpeed);
		}

		if (tab == 4)
		{
			ZeroGui::next_column(30.0f);
			ZeroGui::text_normal(_(" "));
			ZeroGui::check_box(_("Show FOV"), &Settings::ShowFov);
			ZeroGui::check_box(_("Show Crosshair"), &Settings::Crosshair);
		}
		ZeroGui::draw_filled_rect(ImVec2(ZeroGui::cursor_pos().x, ZeroGui::cursor_pos().y), 8, 8, IM_COL32(63.75, 63.75, 63.75, 255));

		if (GetAsyncKeyState(VK_LBUTTON))
		{
			ZeroGui::Input::mouseDown[0] = true;
			ZeroGui::Input::mouseDown[1] = true;
		}
		else
		{
			ZeroGui::Input::mouseDown[0] = false;
			ZeroGui::Input::mouseDown[1] = false;
		}
	}

	ZeroGui::zero_render();

	ImGui::End();
}
