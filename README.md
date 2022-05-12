Gui, -MinimizeBox +HwndChatVoo
Gui, Color, CCCCCC
Gui, Margin, 10, 10
Gui, Font, s12 Bold, Calibri
Gui, Add, Edit, -E0x200 Center Border w300 h300 -VScroll
Gui, Show
Global SaveWinID := {}
Title := "ahk_class QWidget ahk_exe voobly.exe"
Return

::IDK::I don't know
::AYS::Are you sure about that?
::AFAIK::As far as I know
::HTH::Hope this helps
::Hi::Hi buddy!, how it is going?
::INSH::I need some help here!
::AFK::Away from keyboard
::BRB::Be right back
::DC::Disconnected
::GG::Good Game
::GGP::Gotta go pee
::GTG::Good to go
::IGTG::I got to go
::IRL::In real life
::OTW::On the way
::TTYL::Talk to you later
::a1::1 Yes
::a2::2 No
::a3::3 Food, please
::a4::4 Wood, please
::a5::5 Gold, PLease
::a6::6 Stone, please
::a7::7 Ahh
::a8::8 All hail
::a9::9 Oooh
::a10::10 Back to Age 1
::a11::11 Herb laugh
::a12::12 Being rushed
::a13::13 Blame your isp
::a14::14 Start the game already
::a15::15 Don't Point That Thing
::a16::16 Enemy Sighted
::a17::17 It Is Good
::a18::18 I Need a Monk
::a19::19 Long Time No Siege
::a20::20 My granny
::a21::21 Nice Town I'll Take It
::a22::22 Quit Touchin
::a23::23 Raiding Party
::a24::24 Dadgum
::a25::25 Smite Me
::a26::26 The wonder
::a27::27 You play 2 hours
::a28::28 You Should See the Other Guy
::a29::29 Roggan
::a30::30 Wololo
::a31::31 Attack an Enemy Now
::a32::32 Cease Creating Extra Villagers
::a33::33 Create Extra Villagers
::a34::34 Build a Navy
::a35::35 Stop Building a Navy
::a36::36 Wait for My Signal to Attack
::a37::37 Build a Wonder
::a38::38 Give Me Your Extra Resources
::a39::39 Ally
::a40::40 Enemy
::a41::41 Neutral
::a42::42 What Age Are You In

GUIClose:
ExitApp

#If WinActive(Title) || WinActive("ahk_exe age2_x1.exe")
^!V::
	FocusOnChatBar(Title)
	SendTheText()
Return
#If

SendTheText() {
	For Each, Line in StrSplit(Clipboard, "`n") {
		SendInput, % "{Raw}" Line "`n"
	}
}

FocusOnChatBar(Title) {
	WinGet, Hwnd, ID, % Title
	If (SaveWinID[Hwnd] != "") {
		ControlClick, % SaveWinID[Hwnd], % Title
	} Else {
		WinGet, CtrlList, ControlList, % Title
		If (CtrlList) {
			For Each, Ctr in StrSplit(CtrlList, "`n") {
				ControlGetText, ThisText, % Ctr, % Title
				ControlGetPos,,,, Height, % Ctr, % Title
				If (ThisText ~= "input|qt_scrollarea_viewport") && (Height ~= "31|54|56") {
					ControlClick, % Ctr, % Title
					SaveWinID[Hwnd] := Ctr
					Break
				}
			}
		}
	}
}

;<Ping of 16 B x 1 sent on 'default' ... waiting response...>
;<Ping response from hangyapete in 109 ms [direct]>
;<Ping response from ringyo in 109 ms [direct]>
;<Ping response from TheMustache in 203 ms [direct]>
;<Ping response from Biner_ in 250 ms [direct]>


