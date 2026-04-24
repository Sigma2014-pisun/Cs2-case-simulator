<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes, maximum-scale=2.0">
    <title>💰 Рублёвый Кликер — Магазин усилений</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #1a2f1f 0%, #2b4a2c 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            padding: 20px;
            margin: 0;
        }

        .game-container {
            max-width: 650px;
            width: 100%;
            background: rgba(255, 248, 235, 0.9);
            backdrop-filter: blur(20px);
            border-radius: 48px;
            padding: 25px 20px 30px;
            box-shadow: 0 30px 50px rgba(0, 0, 0, 0.5), inset 0 2px 8px rgba(255, 255, 200, 0.6);
            border: 2px solid #c9a03a;
            display: flex;
            flex-direction: column;
            gap: 22px;
        }

        .balance-panel {
            background: #2d2d1c;
            border-radius: 100px;
            padding: 15px 25px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 10px 15px rgba(0,0,0,0.4), inset 0 2px 5px rgba(255,255,180,0.7);
            border: 1px solid #e6b422;
            color: #ffd966;
            flex-wrap: wrap;
            gap: 10px;
        }

        .balance-label {
            font-size: 1.2rem;
            font-weight: bold;
            letter-spacing: 1px;
            text-transform: uppercase;
            color: #ebc77e;
        }

        .balance-amount {
            font-size: 2.8rem;
            font-weight: 800;
            background: #0f1a0b;
            padding: 5px 25px;
            border-radius: 60px;
            color: #f9e076;
            text-shadow: 0 0 10px #ffb703;
            box-shadow: inset 0 0 10px #000000;
            line-height: 1.2;
        }

        .per-click-indicator {
            background: #4a3b1f;
            border-radius: 30px;
            padding: 5px 15px;
            font-weight: bold;
            color: #ffd966;
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 1.1rem;
        }

        .click-area {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 10px 0 5px;
        }

        .coin-button {
            background: radial-gradient(circle at 40% 35%, #f9e076, #b8860b);
            border: none;
            width: 180px;
            height: 180px;
            border-radius: 50%;
            box-shadow: 0 20px 30px rgba(0,0,0,0.6), 0 0 0 8px #f1c40f, 0 0 0 14px #b47c2e;
            font-size: 3.5rem;
            font-weight: bold;
            color: #2d1f00;
            cursor: pointer;
            transition: all 0.07s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            text-shadow: 2px 2px 0 rgba(255,255,200,0.8);
            user-select: none;
            position: relative;
            background-size: 100% 100%;
        }

        .coin-button:active {
            transform: scale(0.88);
            box-shadow: 0 10px 15px rgba(0,0,0,0.7), 0 0 0 5px #f1c40f, 0 0 0 10px #b47c2e;
            background: radial-gradient(circle at 40% 35%, #ffe28c, #a67c1e);
        }

        .coin-button span {
            display: block;
            margin-top: 5px;
        }

        .shop-title {
            font-size: 1.7rem;
            font-weight: 700;
            color: #3b2b0f;
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 5px;
            border-bottom: 3px dashed #c9a03a;
            padding-bottom: 5px;
        }

        .upgrades-grid {
            display: flex;
            flex-direction: column;
            gap: 15px;
            max-height: 350px;
            overflow-y: auto;
            padding-right: 5px;
        }

        .upgrade-card {
            background: #fef7e0;
            border-radius: 28px;
            padding: 14px 18px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 6px 12px rgba(0,0,0,0.25);
            border: 2px solid #d4a017;
            transition: all 0.2s;
            flex-wrap: wrap;
            gap: 10px;
        }

        .upgrade-card.owned {
            background: #d4c29b;
            border-color: #7b5e1c;
            opacity: 0.9;
        }

        .upgrade-info {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .upgrade-name {
            font-weight: 700;
            font-size: 1.2rem;
            color: #3b2b0f;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .upgrade-desc {
            font-size: 0.85rem;
            color: #5e4a23;
        }

        .buy-button {
            background: #28a745;
            border: none;
            border-radius: 40px;
            padding: 12px 22px;
            font-weight: bold;
            font-size: 1rem;
            color: white;
            background: linear-gradient(180deg, #2ecc71 0%, #1e7b34 100%);
            box-shadow: 0 6px 0 #0f4a1a, 0 4px 10px black;
            cursor: pointer;
            transition: 0.08s linear;
            border: 1px solid #90ee90;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            white-space: nowrap;
        }

        .buy-button:active {
            transform: translateY(4px);
            box-shadow: 0 2px 0 #0f4a1a, 0 4px 8px black;
        }

        .buy-button:disabled {
            background: #6c757d;
            box-shadow: 0 4px 0 #343a40;
            border-color: #aaa;
            cursor: not-allowed;
            opacity: 0.7;
            transform: none;
        }

        .stats-row {
            display: flex;
            justify-content: space-between;
            color: #3b3b1a;
            font-weight: 500;
            background: #f5e7c8;
            border-radius: 30px;
            padding: 8px 18px;
        }

        .reset-area {
            display: flex;
            justify-content: flex-end;
        }

        .reset-btn {
            background: none;
            border: 2px solid #c47b2e;
            background: #ffe7c4;
            border-radius: 30px;
            padding: 8px 18px;
            font-weight: bold;
            color: #784b1f;
            cursor: pointer;
            transition: 0.2s;
        }

        .reset-btn:hover {
            background: #f3cd81;
        }

        @media (max-width: 450px) {
            .balance-amount {
                font-size: 2rem;
                padding: 5px 15px;
            }
            .coin-button {
                width: 140px;
                height: 140px;
                font-size: 2.8rem;
            }
        }
    </style>
</head>
<body>
<div class="game-container">
    <!-- Баланс -->
    <div class="balance-panel">
        <span class="balance-label">💵 РУБЛИ</span>
        <span class="balance-amount" id="balanceDisplay">1</span>
        <div class="per-click-indicator">
            <span>🖱️</span> <span id="clickPowerDisplay">1</span> ₽/клик
        </div>
    </div>

    <!-- Кликабельная монета -->
    <div class="click-area">
        <button class="coin-button" id="mainCoin">
            <span>🪙</span>
        </button>
    </div>

    <!-- Статистика -->
    <div class="stats-row">
        <span>📦 Всего кликов: <span id="totalClicksDisplay">0</span></span>
        <span>✨ Усилений куплено: <span id="upgradesCountDisplay">0</span></span>
    </div>

    <!-- Магазин -->
    <div>
        <div class="shop-title">
            <span>🛒 МАГАЗИН УСИЛЕНИЙ</span>
        </div>
        <div class="upgrades-grid" id="shopContainer">
            <!-- Карточки генерируются динамически -->
        </div>
    </div>

    <!-- Сброс -->
    <div class="reset-area">
        <button class="reset-btn" id="resetButton">🔄 Сбросить прогресс</button>
    </div>
</div>

<script>
    (function() {
        // ---------- СОСТОЯНИЕ ИГРЫ ----------
        const GameState = {
            balance: 1,                // текущие рубли
            baseClickValue: 1,        // базовая ценность клика (1 рубль)
            totalClicks: 0,
            // Массив купленных улучшений (храним id и количество, но у нас каждое улучшение можно купить только 1 раз)
            ownedUpgrades: new Set(),  // хранит id купленных улучшений
        };

        // ---------- КОНФИГУРАЦИЯ УЛУЧШЕНИЙ (МАГАЗИН) ----------
        const upgrades = [
            {
                id: 'double_tap',
                name: '🔁 Двойной удар',
                baseDescription: 'Каждый клик приносит +1 рубль.',
                baseCost: 15,
                // эффект: увеличивает клик на +1 (навсегда)
                applyEffect: (state) => {
                    state.baseClickValue += 1;
                },
                // описание после покупки можно менять, но будем динамически показывать
            },
            {
                id: 'lucky_coin',
                name: '🍀 Монетка удачи',
                baseDescription: 'Увеличивает доход с клика на +3 рубля.',
                baseCost: 45,
                applyEffect: (state) => {
                    state.baseClickValue += 3;
                },
            },
            {
                id: 'silver_spoon',
                name: '🥄 Серебряная ложка',
                baseDescription: 'Добавляет +7 рублей за клик.',
                baseCost: 110,
                applyEffect: (state) => {
                    state.baseClickValue += 7;
                },
            },
            {
                id: 'gold_tooth',
                name: '🦷 Золотой зуб',
                baseDescription: 'Мощный бонус: +15 рублей за клик.',
                baseCost: 280,
                applyEffect: (state) => {
                    state.baseClickValue += 15;
                },
            },
            {
                id: 'diamond_ring',
                name: '💍 Бриллиантовое кольцо',
                baseDescription: 'Роскошный бонус: +35 рублей за клик.',
                baseCost: 700,
                applyEffect: (state) => {
                    state.baseClickValue += 35;
                },
            },
            {
                id: 'crown_emperor',
                name: '👑 Императорская корона',
                baseDescription: 'Элитное усиление: +80 рублей за клик.',
                baseCost: 1800,
                applyEffect: (state) => {
                    state.baseClickValue += 80;
                },
            },
            {
                id: 'ruby_crystal',
                name: '🔮 Рубиновый кристалл',
                baseDescription: 'Магический бонус: +200 рублей за клик.',
                baseCost: 5000,
                applyEffect: (state) => {
                    state.baseClickValue += 200;
                },
            },
        ];

        // ---------- ВСПОМОГАТЕЛЬНЫЕ ФУНКЦИИ ----------
        function saveGame() {
            const saveData = {
                balance: GameState.balance,
                baseClickValue: GameState.baseClickValue,
                totalClicks: GameState.totalClicks,
                ownedUpgrades: Array.from(GameState.ownedUpgrades),
            };
            localStorage.setItem('rubleClickerSave', JSON.stringify(saveData));
        }

        function loadGame() {
            const saved = localStorage.getItem('rubleClickerSave');
            if (!saved) return;
            try {
                const data = JSON.parse(saved);
                GameState.balance = data.balance ?? 1;
                GameState.baseClickValue = data.baseClickValue ?? 1;
                GameState.totalClicks = data.totalClicks ?? 0;
                GameState.ownedUpgrades = new Set(data.ownedUpgrades || []);
                // Восстановление эффектов: пересчитываем baseClickValue на основе ownedUpgrades
                // Чтобы избежать дублирования, сбрасываем baseClickValue до 1 и применяем все купленные улучшения заново.
                recalculateClickValueFromOwned();
            } catch (e) {
                console.warn('Ошибка загрузки, сброс');
                resetGame();
            }
        }

        // Пересчитывает baseClickValue, применяя все купленные улучшения
        function recalculateClickValueFromOwned() {
            // Начинаем с 1 (базовый рубль)
            GameState.baseClickValue = 1;
            // Применяем эффекты всех owned улучшений в порядке их id (или как есть)
            for (let upgrade of upgrades) {
                if (GameState.ownedUpgrades.has(upgrade.id)) {
                    upgrade.applyEffect(GameState);
                }
            }
        }

        function resetGame() {
            GameState.balance = 1;
            GameState.baseClickValue = 1;
            GameState.totalClicks = 0;
            GameState.ownedUpgrades.clear();
            saveGame();
            updateUI();
        }

        // Проверка, можно ли купить улучшение
        function canBuyUpgrade(upgrade) {
            if (GameState.ownedUpgrades.has(upgrade.id)) return false;
            return GameState.balance >= upgrade.baseCost;
        }

        // Покупка улучшения
        function buyUpgrade(upgradeId) {
            const upgrade = upgrades.find(u => u.id === upgradeId);
            if (!upgrade) return false;
            if (!canBuyUpgrade(upgrade)) return false;

            // Списываем деньги
            GameState.balance -= upgrade.baseCost;
            // Добавляем в owned
            GameState.ownedUpgrades.add(upgrade.id);
            // Применяем эффект (увеличиваем baseClickValue)
            upgrade.applyEffect(GameState);

            saveGame();
            updateUI();
            return true;
        }

        // Обработка клика по монете
        function handleCoinClick() {
            // Добавляем деньги равные текущей силе клика
            GameState.balance += GameState.baseClickValue;
            GameState.totalClicks += 1;
            saveGame();
            updateUI();
            // Небольшая анимация/отклик (звук не добавляем, чисто визуал)
        }

        // ---------- РЕНДЕРИНГ ИНТЕРФЕЙСА ----------
        const balanceDisplay = document.getElementById('balanceDisplay');
        const clickPowerDisplay = document.getElementById('clickPowerDisplay');
        const totalClicksDisplay = document.getElementById('totalClicksDisplay');
        const upgradesCountDisplay = document.getElementById('upgradesCountDisplay');
        const shopContainer = document.getElementById('shopContainer');
        const mainCoin = document.getElementById('mainCoin');
        const resetButton = document.getElementById('resetButton');

        function updateUI() {
            // Обновляем текстовые значения
            balanceDisplay.textContent = GameState.balance;
            clickPowerDisplay.textContent = GameState.baseClickValue;
            totalClicksDisplay.textContent = GameState.totalClicks;
            upgradesCountDisplay.textContent = GameState.ownedUpgrades.size;

            // Перестраиваем магазин
            renderShop();
        }

        function renderShop() {
            if (!shopContainer) return;
            shopContainer.innerHTML = '';

            upgrades.forEach(upgrade => {
                const isOwned = GameState.ownedUpgrades.has(upgrade.id);
                const canBuy = !isOwned && GameState.balance >= upgrade.baseCost;

                const card = document.createElement('div');
                card.className = `upgrade-card ${isOwned ? 'owned' : ''}`;

                // Описание: базовое описание из конфига
                const desc = upgrade.baseDescription;

                card.innerHTML = `
                    <div class="upgrade-info">
                        <div class="upgrade-name">
                            <span>${upgrade.name}</span>
                            ${isOwned ? '<span style="color:#2e7d32;">✓</span>' : ''}
                        </div>
                        <div class="upgrade-desc">${desc}</div>
                    </div>
                    <button class="buy-button" data-id="${upgrade.id}" ${!canBuy ? 'disabled' : ''}>
                        ${isOwned ? 'КУПЛЕНО' : `💰 ${upgrade.baseCost} ₽`}
                    </button>
                `;

                // Добавляем обработчик на кнопку
                const btn = card.querySelector('.buy-button');
                if (btn && !isOwned) {
                    btn.addEventListener('click', (e) => {
                        e.stopPropagation();
                        const id = btn.getAttribute('data-id');
                        if (id) {
                            buyUpgrade(id);
                        }
                    });
                } else if (btn && isOwned) {
                    // Кнопка неактивна, но оставляем disabled
                    btn.disabled = true;
                }

                shopContainer.appendChild(card);
            });
        }

        // Привязка событий
        mainCoin.addEventListener('click', handleCoinClick);

        resetButton.addEventListener('click', () => {
            if (confirm('Вы уверены, что хотите сбросить весь прогресс? Деньги и усиления пропадут.')) {
                resetGame();
            }
        });

        // Инициализация: загрузка и первый рендер
        loadGame();
        // Дополнительная проверка: если после загрузки ownedUpgrades пуст, а baseClickValue >1 (на всякий случай пересчитаем)
        // Но recalculate уже вызван в loadGame.
        updateUI();

        // Дополнительно: сохраняем при закрытии вкладки (на всякий случай)
        window.addEventListener('beforeunload', () => {
            saveGame();
        });

        // Для удобства: можно также обновлять UI при видимости страницы
        document.addEventListener('visibilitychange', () => {
            if (document.visibilityState === 'visible') {
                // на случай если что-то изменилось в другой вкладке (маловероятно), пересчитаем
                // Но проще просто перерисовать.
                updateUI();
            }
        });

    })();
</script>
</body>
</html>
