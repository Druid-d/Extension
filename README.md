# Extension
Extensions to help focus on programming

This extension uses keywords to blur information that is not related to programming.

Extension Installation:
  1) Open Chrome and go to chrome://extensions/
  2) Enable "Developer mode"
  3) Click "Load unpacked"
  4) Select the programming-filter
  extension folder

If you have suggestions for improving 
the code or updating the filter lists, 
please email me, preferably attaching a 
txt file with your suggestions.

this is current version of the word filter:
const programmingKeywords = [
    // Языки программирования
    'javascript', 'python', 'java', 'c++', 'c#', 'ruby', 'php', 'swift', 'kotlin',
    'go', 'rust', 'typescript', 'html', 'css', 'sql', 'bash', 'shell', 'perl',
    'scala', 'haskell', 'lua', 'r', 'matlab', 'dart',
    
   
  // Фреймворки
    'react', 'vue', 'angular', 'node.js', 'django', 'flask', 'spring', 'laravel',
    'rails', 'express', 'next.js', 'svelte', 'jquery', 'bootstrap', 'tailwind',
    'tensorflow', 'pytorch', 'pandas', 'numpy', 'opencv',
    
  // Инструменты
    'docker', 'kubernetes', 'aws', 'azure', 'git', 'github', 'gitlab', 'jenkins',
    'linux', 'nginx', 'apache', 'postgresql', 'mongodb', 'redis', 'mysql',
    'graphql', 'rest api', 'websocket', 'webpack', 'vite',
    
   // Термины
    'algorithm', 'function', 'variable', 'array', 'object', 'class', 'inheritance',
    'recursion', 'sorting', 'database', 'query', 'cache', 'memory', 'pointer',
    'debugging', 'compiling', 'refactoring', 'deployment', 'testing',
    'commit', 'push', 'pull', 'merge', 'branch', 'repository', 'loop', 'iteration',
    'recursion', 'stack', 'queue', 'tree', 'graph', 'hashmap', 'dictionary',
    'api', 'endpoint', 'middleware', 'callback', 'promise', 'async', 'await',
    'thread', 'concurrency', 'parallelism', 'mutex', 'semaphore',
    'code', 'coding', 'programming', 'development', 'software', 'web dev',
    
   // Обучение
    'tutorial', 'documentation', 'stackoverflow', 'leetcode', 'hackerrank',
    'codecademy', 'udemy', 'coursera', 'freecodecamp', 'w3schools', 'mdn',
    'github', 'gitlab', 'bitbucket', 'jira', 'confluence',
    
  // Русские
    'программирование', 'разработка', 'код', 'алгоритм', 'функция',
    'переменная', 'массив', 'объект', 'класс', 'отладка', 'компиляция',
    'рефакторинг', 'деплой', 'тестирование', 'коммит', 'репозиторий',
    'фреймворк', 'библиотека', 'запрос', 'сервер', 'клиент', 'бэкенд', 'фронтенд',
    'цикл', 'условие', 'ветвление', 'рекурсия', 'стек', 'очередь'
];

// ❌ ЧЁРНЫЙ СПИСОК: термины из других наук (АНГЛИЙСКИЕ + РУССКИЕ)
const nonProgrammingKeywords = [
    // ==================== БИОЛОГИЯ (ENGLISH) ====================
    'biology', 'biological', 'cell', 'cellular', 'dna', 'rna', 'gene', 'genetics',
    'evolution', 'species', 'population', 'homeostasis', 'metabolism', 'photosynthesis',
    'mitochondria', 'organelle', 'cytoplasm', 'membrane', 'protein', 'enzyme',
    'hormone', 'neuron', 'synapse', 'ecosystem', 'biosphere', 'biome', 'habitat',
    'symbiosis', 'parasite', 'bacteria', 'virus', 'fungus', 'algae', 'plant',
    'animal', 'mammal', 'reptile', 'amphibian', 'embryology', 'anatomy',
    'physiology', 'cytology', 'histology', 'microbiology', 'biochemistry',
    'biophysics', 'biotechnology', 'clone', 'stem cell', 'sequencing',
    'chromosome', 'mitosis', 'meiosis', 'ribosome', 'lysosome', 'golgi',
    
   // ==================== ФИЗИКА (ENGLISH) ====================
    'physics', 'physical', 'quantum', 'relativistic', 'gravity', 'gravitational',
    'electromagnetism', 'thermodynamics', 'entropy', 'energy', 'momentum',
    'force', 'mass', 'velocity', 'acceleration', 'particle', 'atom', 'electron',
    'proton', 'neutron', 'photon', 'boson', 'fermion', 'quark', 'field',
    'wave', 'frequency', 'wavelength', 'interference', 'diffraction',
    'polarization', 'quantization', 'entanglement', 'superposition',
    'black hole', 'singularity', 'big bang', 'cosmology', 'astrophysics',
    'mechanics', 'kinematics', 'dynamics', 'thermodynamic', 'adiabatic',
    
  // ==================== ХИМИЯ (ENGLISH) ====================
    'chemistry', 'chemical', 'molecule', 'periodic table', 'element',
    'compound', 'reaction', 'catalysis', 'solution', 'acid', 'base', 'alkali',
    'oxidation', 'reduction', 'covalent bond', 'ionic bond', 'hydrogen bond',
    'osmosis', 'diffusion', 'polymer', 'monomer', 'crystal', 'amorphous',
    'organic chemistry', 'inorganic chemistry', 'analytical chemistry',
    'stoichiometry', 'mole', 'avogadro', 'enthalpy', 'gibbs free energy',    
    
  // ==================== МАТЕМАТИКА (ENGLISH) ====================
    'mathematics', 'mathematical', 'theorem', 'proof', 'axiom', 'lemma',
    'topology', 'algebra', 'geometry', 'trigonometry', 'differentiation',
    'integration', 'derivative', 'integral', 'limit', 'series', 'matrix',
    'vector', 'tensor', 'complex number', 'differential equation',
    'calculus', 'statistics', 'probability', 'distribution', 'variance',
    
  // ==================== ИСТОРИЯ (ENGLISH) ====================
    'history', 'historical', 'war', 'revolution', 'empire', 'king', 'queen',
    'emperor', 'president', 'dictator', 'medieval', 'ancient', 'renaissance',
    'enlightenment', 'colonization', 'slavery', 'feudalism', 'capitalism',
    'socialism', 'communism', 'archaeology', 'paleontology', 'anthropology',
    
   // ==================== ГЕОГРАФИЯ (ENGLISH) ====================
    'geography', 'geological', 'continent', 'ocean', 'sea', 'river', 'mountain',
    'desert', 'climate', 'weather', 'atmosphere', 'lithosphere', 'hydrosphere',
    'tectonics', 'earthquake', 'volcano', 'mineral', 'crystal', 'sediment',
    
   // ==================== АСТРОНОМИЯ (ENGLISH) ====================
    'astronomy', 'astronomical', 'planet', 'star', 'galaxy', 'nebula',
    'comet', 'asteroid', 'meteorite', 'orbit', 'telescope', 'spectrum',
    'cosmology', 'universe', 'black hole', 'supernova', 'pulsar', 'quasar',
    'exoplanet', 'constellation', 'solar system', 'milky way',
    
  // ==================== МЕДИЦИНА (ENGLISH) ====================
    'medicine', 'medical', 'disease', 'symptom', 'diagnosis', 'treatment',
    'therapy', 'surgery', 'drug', 'medication', 'antibiotic', 'vaccine',
    'patient', 'doctor', 'physician', 'hospital', 'clinic', 'pharmacy',
    'infection', 'inflammation', 'cancer', 'tumor', 'diabetes', 'hypertension',
    
  // ==================== ПСИХОЛОГИЯ (ENGLISH) ====================
    'psychology', 'psychological', 'consciousness', 'subconscious', 'behavior',
    'emotion', 'feeling', 'perception', 'memory', 'learning', 'motivation',
    'personality', 'character', 'temperament', 'stress', 'anxiety', 'depression',
    'schizophrenia', 'psychoanalysis', 'cognitive', 'behavioral',
    
  // ==================== ФИЛОСОФИЯ (ENGLISH) ====================
    'philosophy', 'philosophical', 'ethics', 'morality', 'epistemology',
    'metaphysics', 'ontology', 'logic', 'truth', 'existence', 'reality',
    'existentialism', 'stoicism', 'nihilism',
    
   // ==================== РУССКИЕ ТЕРМИНЫ (все науки) ====================
    'биология', 'биологический', 'клетка', 'днк', 'генетика', 'эволюция',
    'гомеостаз', 'фотосинтез', 'митохондрия', 'физика', 'квантовый', 'гравитация',
    'термодинамика', 'энтропия', 'химия', 'молекула', 'реакция', 'катализ',
    'математика', 'теорема', 'интеграл', 'производная', 'история', 'война',
    'революция', 'география', 'континент', 'океан', 'астрономия', 'планета',
    'галактика', 'медицина', 'болезнь', 'лечение', 'психология', 'сознание',
    'философия', 'этика', 'метафизика', 'искусство', 'музыка', 'литература'
];
