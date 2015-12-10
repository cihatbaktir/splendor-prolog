:- module(simple2014800018, []).
/*
:- dynamic cards/1.
:- dynamic tickets/1.

cards([]).
tickets([]).
*/
:-dynamic cardlist/1.
initialize(PlayerName, PlayerCount) :-
	show(1, 'I am ~w of a ~w player game.~n', [PlayerName, PlayerCount]).

getGems(_,_).
buyCard(_).
reserveCard(_).
reserveCardFromDeck(_).

decideAction(Player, Oponents, StateProxy, Action) :-
	call(StateProxy, Player, gems, Gems),
	call(StateProxy, Player, bonuses, Bonuses),
	call(StateProxy, Player, reserves, Reserves),
	call(StateProxy, game, cards, Cards),!,
	(
		length(Reserves, ReservesLength),
		ReservesLength<3,
		random(1,11,1),
		length(Cards, CardsLength),
		CardsLength1 is CardsLength+1,
		random(1, CardsLength1, ReserveId),
		nth1(ReserveId, Cards, ReservedCard),
		Action = reserveCard(ReservedCard)
		;
		canBuyCards(Gems, Bonuses, Cards, CanBuyCards),
		nth1(1, CanBuyCards, CardId),
		Action = buyCard(CardId)
		;
		display('a'),
		call(StateProxy, game, tokens, Tokens),
		display('b'),
		card(CardId, NeededGems-_-_),!,
		display('c'),
		splendor:card(CardId, NeededGems-_-_),
		display('d'),
		splendor:addGems(Gems, Bonuses, TotalGems),
		display('e'),
		splendor:subtractGems(TotalGems, NeededGems, RemainingGems),
		display('f'),
		%splendor:minusGemTotal(RemainingGems, MinusTotal),
	%show(40, 'Minus total: ~w~n', [MinusTotal]),
		display('g'),
		AimCard is CardId, 
		display('h'),
		splendor:card(AimCard,NeedGem-_-_),
		print(NeedGem),
		display('i'),
		nth1(1,NeedGem,X),nth1(2,NeedGem,Y),nth1(3,NeedGem,Z),nth1(4,NeedGem,A),nth1(5,NeedGem,B),
		nth1(1,Gems, C),nth1(2,Gems, D),nth1(3,Gems, E),nth1(4,Gems, F),nth1(5,Gems, G),
		display('j'),
		(X > C, assert(cardlist([2,0,0,0,0,0]));Y>D,assert(cardlist([0,2,0,0,0,0])); Z>E, assert(cardlist([0,0,2,0,0,0]));
		A > F, assert(cardlist([0,0,0,2,0,0])); B>G,assert(cardlist([0,0,0,0,2,0]))),
		display('k'),
		cardlist(K),
		splendor:randomlyGetGems(Gems, Tokens, K, BackGems),
		Action = getGems(K, BackGems)
	)
	,member(Oponent, Oponents)
	,call(StateProxy, Oponent, score, _)
	.

selectNoble([H|_],H).

canBuyCards(_, _, [], []).

canBuyCards(Gems, Bonuses, [H|T], A) :-
	(
		canBuyCard(Gems, Bonuses, H),
		A = [H|X2]
		;
		A=X2
	),
	canBuyCards(Gems, Bonuses, T, X2)
	.



randomTest(A) :-
	A=3,
	display('hi there'),
	repeat,
	random(1, 10000000, X),
	X<5,
	!.
