export default async function handler(req, res) {
  // CORS
  res.setHeader('Access-Control-Allow-Origin', '*');
  res.setHeader('Access-Control-Allow-Methods', 'POST, OPTIONS');
  res.setHeader('Access-Control-Allow-Headers', 'Content-Type');

  if (req.method === 'OPTIONS') return res.status(200).end();
  if (req.method !== 'POST') return res.status(405).json({ error: 'Method not allowed' });

  try {
    const { topTalents, allScores } = req.body;

    const topList = topTalents.map((t, i) => `${i + 1}. ${t.name} (${t.desc})`).join('\n');
    const allList = Object.entries(allScores)
      .sort((a, b) => b[1] - a[1])
      .map(([t, s]) => `${t}: ${s}`)
      .join(', ');

    const prompt = `Ти — провідний коуч з розвитку особистості та кар'єри. Проведи глибокий аналіз профілю людини за результатами тесту сильних сторін.

ТОП-5 ТАЛАНТІВ ЛЮДИНИ:
${topList}

ПОВНИЙ ПРОФІЛЬ БАЛІВ:
${allList}

Напиши детальний персональний аналіз УКРАЇНСЬКОЮ МОВОЮ у такій структурі:

### Твоя суть
2-3 речення про те, хто ця людина в своїй основі — яка її природа, як вона сприймає світ.

### Як працюють твої топ-5 разом
Поясни, як ці п'ять талантів взаємодіють і підсилюють одне одного. Конкретно і образно.

### Твої суперсили
Перелічи 3-4 конкретні ситуації або завдання, де ця людина природно перевершує інших.

### Сліпі зони
Чесно назви 2-3 патерни або ризики, які виникають через ці таланти. Не критика — розуміння.

### Кар'єра і роль
Які ролі, сфери або типи роботи найкраще розкривають цей профіль? Конкретні приклади.

### Для команди
Як ця людина найкраще взаємодіє з іншими? З ким доповнює, з ким конфліктує?

### Три кроки розвитку
Три конкретних практичних дії, які ця людина може зробити вже цього тижня для розвитку своїх сильних сторін.

Тон: глибокий, щирий, без шаблонних фраз. Як від мудрого ментора.`;

    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'x-api-key': process.env.ANTHROPIC_API_KEY,
        'anthropic-version': '2023-06-01',
      },
      body: JSON.stringify({
        model: 'claude-sonnet-4-5',
        max_tokens: 2500,
        messages: [{ role: 'user', content: prompt }],
      }),
    });

    const data = await response.json();
    const text = data.content?.[0]?.text || 'Не вдалось отримати аналіз.';
    res.status(200).json({ analysis: text });

  } catch (err) {
    console.error(err);
    res.status(500).json({ error: 'Internal server error' });
  }
}
