---
title: Цепочки-осколки
description: Узнайте о цепочках-осколках - разделах сети, которые дают Ethereum большую пропускную способность транзакций и облегчают его запуск.
lang: ru
template: eth2
sidebar: true
image: ../../../../../assets/eth2/newrings.png
summaryPoint1: Шардинг представляет собой многоэтапную модернизацию, чтобы улучшить масштабируемость и емкость Ethereum.
summaryPoint2: Цепочки-осколки распределяют нагрузку в сети на 64 новые цепочки.
summaryPoint3: Они упрощают запуск узла за счет низких аппаратных требований.
summaryPoint4: Технические дорожные карты включают в себя работу над цепочками-осколками в "Фазе 1" и потенциально "Фазе 2."
---

<UpgradeStatus dateKey="page-eth2-upgrades-shards-date">
    Цепочки-осколки должны быть запущены где-то в 2023 году в зависимости от того, как быстро продвигается работа после запуска <a href="/eth2/beacon-chain/">Beacon Chain</a>. Эти осколки дадут Ethereum больше возможностей для хранения и доступа к данным, но они не будут использоваться для выполнения кода. Подробности пока прорабатываются.
</UpgradeStatus>

## Что такое шардинг? {#what-is-sharding}

Шардинг – это процесс разделения базы данных по горизонтали для распределения нагрузки, распространенная концепция в информатике. В контексте Ethereum шардинг уменьшит перегрузку сети и увеличит количество транзакций в секунду за счет создания новых цепочек, известных как "осколки".

Это важно по причинам, отличным от масштабируемости.

## Особенности шардинга {#features-of-sharding}

### Каждый может запустить узел {#everyone-can-run-a-node}

Шардинг - это хороший способ масштабирования, если вы хотите сохранить децентрализацию, поскольку альтернативой является масштабирование путем увеличения размера существующей базы данных. Это сделало бы Ethereum менее доступным для валидаторов сети, потому что им понадобились бы более мощные и дорогие компьютеры. В цепочках-осколках валидаторам нужно хранить/запускать данные только для того сегмента, который они проверяют, а не для всей сети (как это происходит сегодня). Это ускоряет процесс и резко снижает требования к оборудованию.

### Более активное участие в сети {#more-network-participation}

Шардинг в конечном итоге позволит вам запускать Ethereum на личном ноутбуке или телефоне. Таким образом, больше людей должны иметь возможность участвовать или запускать [клиенты](/developers/docs/nodes-and-clients/) в сегментированном Ethereum. Это повысит безопасность, потому что чем более децентрализована сеть, тем меньше площадь поверхности атаки.

При более низких требованиях к оборудованию шардинг упростит запуск [клиентов](/developers/docs/nodes-and-clients/) самостоятельно, не полагаясь вообще ни на какие посреднические услуги. И если вы можете, подумайте о запуске нескольких клиентов. Это может улучшить работоспособность сети за счет дальнейшего сокращения точек сбоя. [Запустите клиент Eth2](/eth2/get-involved/)

<br />

<InfoBanner isWarning={true}>
  Во-первых, вам нужно запустить клиент основной сети в то же время, как и ваш клиент для eth2. <a href="https://launchpad.ethereum.org" target="_blank">Панель запуска</a> проведет вас через требования к оборудованию и процесс. В качестве альтернативы вы можете использовать <a href="/developers/docs/apis/backend/#available-libraries">внутренний API</a>.
</InfoBanner>

## Цепочки-осколки версии 1: доступность данных {#data-availability}

Когда первые цепочки-осколки будут запущены, они просто предоставят дополнительные данные в сеть. Они не будут обрабатывать транзакции или смарт-контракты. Но они все равно значительно повысят количество обрабатываемых транзакций в секунду в сочетании со свертками.

Сверток - это технология второго слоя, которая существует сегодня. Они позволяют децентрализованным приложениям комбинировать или «сворачивать» транзакции в одну транзакцию вне цепи, генерировать криптографическое доказательство и затем передать их в цепочку. Это уменьшает объем данных, необходимых для транзакции. Объедините это со всей дополнительной доступностью данных, обеспечиваемой осколками, и вы получите 100 000 транзакций в секунду.

[Подробнее о свертках](/developers/docs/layer-2-scaling/)

## Цепочки-осколки версии 2: выполнение кода {#code-execution}

План всегда состоял в том, чтобы добавить дополнительную функциональность к осколкам, чтобы сделать их более похожими на [основную сеть Ethereum](/glossary/#mainnet). Это позволит им хранить и исполнять смарт-контракты и обрабатывать учетные записи. Но учитывая увеличение транзакций в секунду, которое обеспечивают цепочки-осколки версии 1, нужно ли это еще? Это все еще обсуждается в сообществе, и, похоже, есть несколько вариантов.

### Нужны ли осколки для выполнения кода? {#do-shards-need-code-execution}

Виталик Бутерин в разговоре с подкастом Bankless представил три потенциальных варианта, которые стоит обсудить.

<YouTube id="-R0j5AMUSzA" start="5841" />

#### 1. Исполнение состояния не требуется {#state-execution-not-needed}

Это означало бы, что мы не даем осколкам возможности обрабатывать смарт-контракты и оставляем их в качестве хранилищ данных.

#### 2. Иметь несколько исполнительных осколков {#some-execution-shards}

Возможно, есть компромисс, когда нам не нужно, чтобы все осколки были умными (64 запланированы прямо сейчас). Мы могли бы просто добавить эту функциональность к нескольким, а остальные оставить как есть. Это может ускорить запуск.

#### 3. Подождать, пока мы не сможем сделать СНАРКи с нулевым разглашением {#wait-for-zk-snarks}

Наконец, возможно, нам следует вернуться к этой дискуссии, когда укрепятся СНАРКи с нулевым разглашением. Это технология, которая может помочь принести действительно конфиденциальные транзакции в сеть. Вполне вероятно, что им потребуются более умные осколки, но они все еще находятся в стадии исследований и разработок.

#### Другие источники {#other-sources}

Вот еще несколько мыслей в том же духе:

- [Фаза первая и готово: Eth2 как механизм доступности данных](https://ethresear.ch/t/phase-one-and-done-eth2-as-a-data-availability-engine/5269/8) – _cdetrio, ethresear.ch_

Этот вопрос до сих пор активно обсуждается. Мы обновим эти страницы, как только узнаем больше.

## Взаимосвязь между обновлениями {#relationship-between-upgrades}

Все обновления Eth2 в некоторой степени взаимосвязаны. Итак, давайте вспомним, как цепочки-осколки связаны с другими обновлениями.

### Осколки и Beacon Chain {#shards-and-beacon-chain}

Beacon Chain содержит всю логику для обеспечения безопасности и синхронизации осколков. Beacon Chain будет координировать стейкеров в сети, распределяя их по осколкам, над которыми они должны работать. И она также облегчит связь между осколками, получая и храня данные транзакций в цепочках-осколках, доступные другим осколкам. Это даст осколкам моментальный снимок состояния в сети Ethereum, чтобы держать все в актуальном состоянии.

<ButtonLink to="/eth2/beacon-chain/">Beacon Chain</ButtonLink>

### Осколки и стыковка {#shards-and-docking}

Основная сеть Ethereum будет существовать так же, как и сегодня, даже после введения осколков. Однако в какой-то момент основная сеть должна будет стать осколком, чтобы она могла перейти к стейкингу. Еще предстоит выяснить, будет ли основная сеть существовать как единственный “умный” осколок, который может обрабатывать выполнение кода, но в любом случае решение должно быть принято на втором этапе шардинга.

<ButtonLink to="/eth2/docking/">Стыковка</ButtonLink>

<Divider />

### Подробнее {#read-more}

<Eth2ShardChainsList />
