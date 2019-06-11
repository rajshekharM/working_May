# working_May

(tvm_env) raj@raj-VirtualBox:~/tvm/nnvm/tutorials/nlp$ python keras_s2s_translate.py
Using TensorFlow backend.
File /home/raj/.tvm_test_data/keras/s2s_translate.h5 exists, skip.
File /home/raj/.tvm_test_data/data/fra-eng.txt exists, skip.
WARNING:tensorflow:From /home/raj/.local/lib/python3.6/site-packages/tensorflow/python/framework/op_def_library.py:263: colocate_with (from tensorflow.python.framework.ops) is deprecated and will be removed in a future version.
Instructions for updating:
Colocations handled automatically by placer.
2019-06-11 13:56:22.169434: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2
2019-06-11 13:56:22.175880: I tensorflow/core/platform/profile_utils/cpu_utils.cc:94] CPU Frequency: 2495995000 Hz
2019-06-11 13:56:22.176322: I tensorflow/compiler/xla/service/service.cc:150] XLA service 0x55a6c1d64c20 executing computations on platform Host. Devices:
2019-06-11 13:56:22.176435: I tensorflow/compiler/xla/service/service.cc:158]   StreamExecutor device (0): <undefined>, <undefined>
WARNING:tensorflow:From /home/raj/.local/lib/python3.6/site-packages/tensorflow/python/ops/math_ops.py:3066: to_int32 (from tensorflow.python.ops.math_ops) is deprecated and will be removed in a future version.
Instructions for updating:
Use tf.cast instead.
WARNING:tensorflow:From /home/raj/.local/lib/python3.6/site-packages/tensorflow/python/ops/math_grad.py:102: div (from tensorflow.python.ops.math_ops) is deprecated and will be removed in a future version.
Instructions for updating:
Deprecated in favor of operator or tf.math.divide.
Cannot find config for target=llvm, workload=('dense', (1, 256, 'float32'), (1024, 256, 'float32'), (1024, 'float32'), 0). A fallback configuration is used, which may bring great performance regression.
WARNING:autotvm:Cannot find config for target=llvm, workload=('dense', (1, 71, 'float32'), (1024, 71, 'float32'), 0, 0). A fallback configuration is used, which may bring great performance regression.
Encoder build ok.
WARNING:autotvm:Cannot find config for target=llvm, workload=('dense', (1, 94, 'float32'), (1024, 94, 'float32'), 0, 0). A fallback configuration is used, which may bring great performance regression.
WARNING:autotvm:Cannot find config for target=llvm, workload=('dense', (1, 256, 'float32'), (94, 256, 'float32'), (94, 'float32'), 0). A fallback configuration is used, which may bring great performance regression.
Decoder build ok.
1 :  We should help. ==> Nous devrions manger.
2 :  His nose bled. ==> Il saignait du nez.
3 :  I've got eyes. ==> Je suis pourvu d'yeux.
4 :  They're brave. ==> Ils sont courageux.
5 :  Don't freak out. ==> Ne soyez pas seules !
6 :  I have proof. ==> Je dispose d'une preuve.
7 :  I want to stay. ==> Je veux rester.
8 :  I burned it. ==> Je l'ai brûlé.
9 :  I'm the boss. ==> Je suis la patronne.
10 :  It's the truth. ==> C'est la vérité.
11 :  I went inside. ==> J'y ai pénétré.
12 :  It's all wet. ==> Tout est mouillé.
13 :  This is pretty. ==> C'est de l'amour.
14 :  I hate it here. ==> Je déteste être ici.
15 :  You're sad. ==> Tu es triste.
16 :  Let's continue. ==> N'y aller !
17 :  Be serious. ==> Soyez sérieuse !
18 :  Warn Tom. ==> Préviens Tom.
19 :  Back off. ==> Retirez-vous.
20 :  He keeps a cat. ==> Il a un chat.
21 :  I'm a dancer. ==> Je suis danseuse.
22 :  Am I talented? ==> Suis-je doté de talent ?
23 :  Are there kids? ==> Y a-t-il des enfants ?
24 :  Come if you can. ==> Mon t-toi à l'échocre !
25 :  Hurry up, girls. ==> Mannez-vous !
26 :  I'm cooking. ==> Je cuisine.
27 :  I know this. ==> Je le sais.
28 :  I'll call them. ==> Je les appellerai.
29 :  I'm so lonely. ==> Je suis si seule.
30 :  Tom hates you. ==> Tom te hait.
31 :  You start. ==> Tu commences.
32 :  Who was here? ==> Qui était ici ?
33 :  Try again. ==> Essaie de nouveau.
34 :  Take a nap. ==> Fais un petit somme !
35 :  I hurried home. ==> Je me suis précipité à la maison.
36 :  Terrific! ==> Formidable !
37 :  Am I wrong? ==> Ai-je tort ?
38 :  Tom's arrived. ==> Tom est arrivé.
39 :  Here we are! ==> Nous y voilà !
40 :  Is it to go? ==> Ça doit partir ?
41 :  Stay awake. ==> Reste debout.
42 :  I feel ashamed. ==> Je me sens honteux.
43 :  Hand it to me. ==> Passe-le-nous !
44 :  Tom confessed. ==> Tom a avoué.
45 :  You stay here. ==> Tu restes ici.
46 :  Get the box. ==> Prenez la boîte.
47 :  I lost the bet. ==> J'ai perdu le pari.
48 :  Keep this. ==> Garde ça.
49 :  Be merciful. ==> Soyez miséricordieuse !
50 :  I hate milk. ==> Je déteste le lait.
51 :  You're kidding! ==> Tu es malpoli !
52 :  Can I trust him? ==> Je vous parentez-vous ?
53 :  Be merciful. ==> Soyez miséricordieuse !
54 :  It's very good. ==> C'est très bien.
55 :  I already ate. ==> J'ai déjà mangé.
56 :  I'm having fun. ==> Je m'amuse.
57 :  You're sloshed. ==> Tu es endormie.
58 :  I ought to go. ==> Il me faut y aller.
59 :  Come in already. ==> onnêtez à l'étite.
60 :  We're closed. ==> Nous sommes fermés.
61 :  She was busy. ==> Elle était occupée.
62 :  I need to know. ==> J'ai besoin de le savoir.
63 :  I was careless. ==> J'étais insouciante.
64 :  I'm divorced. ==> Je suis divorcé.
65 :  That's alright. ==> C'est un risque.
66 :  Take my advice! ==> Prends maintent !
67 :  It is too hot. ==> Il fait trop chaud.
68 :  This is a desk. ==> C'est un stelle.
69 :  She cried. ==> Elle pleura.
70 :  She walks. ==> Elle marche.
71 :  Let's start! ==> Commençons !
72 :  He swindled her. ==> Il détrave une pruve.
73 :  Do you remember? ==> Prrestes-vous ?
74 :  I am not happy. ==> Je ne suis pas content.
75 :  I like cake. ==> J'aime les gâteaux.
76 :  Are you insured? ==> Tvez-vous sérieux ?
77 :  No one noticed. ==> Personne n'a bien.
78 :  Leave it there. ==> Laissez-le entrer.
79 :  I enjoy working. ==> J'y ai finé.
80 :  Go away. ==> Pars !
81 :  I'll stop. ==> J'arrêterai.
82 :  We're not old. ==> Nous ne sommes pas vieilles.
83 :  I let it fall. ==> Je l'ai laissé tomber.
84 :  Drink it down. ==> Buvez-le !
85 :  Come up here. ==> Approche.
86 :  Tom trusts me. ==> Tom me fait confiance.
87 :  Do you remember? ==> Prrestes-vous ?
88 :  I feel blue. ==> Je me sens déprimée.
89 :  Is that right? ==> Est-ce exact ?
90 :  I hate flying. ==> Je déteste voler.
91 :  You're lazy. ==> Vous êtes paresseuse.
92 :  Shut the door. ==> Fermez la porte !
93 :  Do you recycle? ==> Pratiquez-vous le recyclage ?
94 :  It is Saturday. ==> C'est samedi.
95 :  Tom is a guest. ==> Tom est grand.
96 :  I keep a diary. ==> Je tiens un journal.
97 :  We're obedient. ==> Nous nous ennuyons.
98 :  I'm home. ==> Je suis chez moi.
99 :  I gave Tom that. ==> J'ai peinté le moinde la voit.
100 :  Leave my house. ==> Laissez-moi cormer !
