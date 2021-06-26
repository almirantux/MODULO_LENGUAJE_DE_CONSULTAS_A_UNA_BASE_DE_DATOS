--
-- PostgreSQL database dump
--

-- Dumped from database version 12.7 (Ubuntu 12.7-0ubuntu0.20.04.1)
-- Dumped by pg_dump version 12.7 (Ubuntu 12.7-0ubuntu0.20.04.1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: articulo; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.articulo (
    idarticulo numeric(8,0) NOT NULL,
    fecha date NOT NULL,
    enlace character varying(80) NOT NULL,
    titulo character varying(80) NOT NULL,
    idnutricionista numeric(8,0) NOT NULL,
    idusuario numeric(6,0)
);


ALTER TABLE public.articulo OWNER TO postgres;

--
-- Name: avisos; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.avisos (
    idavisos numeric(8,0) NOT NULL,
    fecha date NOT NULL,
    imagen character varying(30) NOT NULL,
    enlace character varying(80) NOT NULL,
    idnutricionista numeric(8,0) NOT NULL,
    idusuario numeric(6,0)
);


ALTER TABLE public.avisos OWNER TO postgres;

--
-- Name: ficha_imc; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.ficha_imc (
    idficha numeric(9,0) NOT NULL,
    rut numeric(8,0) NOT NULL,
    dv character varying(1) NOT NULL,
    nombre character varying(80) NOT NULL,
    fecha_nacimiento date NOT NULL,
    email character varying(80) NOT NULL,
    movil numeric(11,0) NOT NULL,
    edad numeric(3,0) NOT NULL,
    peso numeric(3,0) NOT NULL,
    estatura numeric(3,2) NOT NULL,
    imc numeric(5,2) NOT NULL,
    genero numeric(2,0) NOT NULL,
    fechaficha date NOT NULL
);


ALTER TABLE public.ficha_imc OWNER TO postgres;

--
-- Name: genero; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.genero (
    idgenero numeric(2,0) NOT NULL,
    nombre character varying(12)
);


ALTER TABLE public.genero OWNER TO postgres;

--
-- Name: nutricionista; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.nutricionista (
    rut numeric(8,0) NOT NULL,
    nombre character varying(60) NOT NULL,
    email character varying(70) NOT NULL,
    movil numeric(12,0) NOT NULL
);


ALTER TABLE public.nutricionista OWNER TO postgres;

--
-- Name: recetas; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.recetas (
    idreceta numeric(8,0) NOT NULL,
    fecha date NOT NULL,
    enlace character varying(80) NOT NULL,
    contenido character varying(80) NOT NULL,
    idnutricionista numeric(8,0) NOT NULL,
    idusuario numeric(6,0) NOT NULL
);


ALTER TABLE public.recetas OWNER TO postgres;

--
-- Name: usuario; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.usuario (
    idusuario numeric(8,0) NOT NULL,
    movil numeric(15,0) NOT NULL
);


ALTER TABLE public.usuario OWNER TO postgres;

--
-- Name: videos; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.videos (
    idvideos numeric(8,0) NOT NULL,
    fecha date NOT NULL,
    enlace character varying(80) NOT NULL,
    titulo character varying(80) NOT NULL,
    idnutricionista numeric(8,0) NOT NULL,
    idusuario numeric(6,0)
);


ALTER TABLE public.videos OWNER TO postgres;

--
-- Data for Name: articulo; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.articulo (idarticulo, fecha, enlace, titulo, idnutricionista, idusuario) FROM stdin;
\.


--
-- Data for Name: avisos; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.avisos (idavisos, fecha, imagen, enlace, idnutricionista, idusuario) FROM stdin;
\.


--
-- Data for Name: ficha_imc; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.ficha_imc (idficha, rut, dv, nombre, fecha_nacimiento, email, movil, edad, peso, estatura, imc, genero, fechaficha) FROM stdin;
\.


--
-- Data for Name: genero; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.genero (idgenero, nombre) FROM stdin;
\.


--
-- Data for Name: nutricionista; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.nutricionista (rut, nombre, email, movil) FROM stdin;
\.


--
-- Data for Name: recetas; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.recetas (idreceta, fecha, enlace, contenido, idnutricionista, idusuario) FROM stdin;
\.


--
-- Data for Name: usuario; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.usuario (idusuario, movil) FROM stdin;
1	56992303151
\.


--
-- Data for Name: videos; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.videos (idvideos, fecha, enlace, titulo, idnutricionista, idusuario) FROM stdin;
\.


--
-- Name: articulo articulo_idnutricionista_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.articulo
    ADD CONSTRAINT articulo_idnutricionista_key UNIQUE (idnutricionista);


--
-- Name: articulo articulo_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.articulo
    ADD CONSTRAINT articulo_pkey PRIMARY KEY (idarticulo);


--
-- Name: avisos avisos_idnutricionista_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.avisos
    ADD CONSTRAINT avisos_idnutricionista_key UNIQUE (idnutricionista);


--
-- Name: avisos avisos_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.avisos
    ADD CONSTRAINT avisos_pkey PRIMARY KEY (idavisos);


--
-- Name: ficha_imc ficha_imc_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.ficha_imc
    ADD CONSTRAINT ficha_imc_pkey PRIMARY KEY (idficha);


--
-- Name: genero genero_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.genero
    ADD CONSTRAINT genero_pkey PRIMARY KEY (idgenero);


--
-- Name: nutricionista nutricionista_movil_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.nutricionista
    ADD CONSTRAINT nutricionista_movil_key UNIQUE (movil);


--
-- Name: nutricionista nutricionista_nombre_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.nutricionista
    ADD CONSTRAINT nutricionista_nombre_key UNIQUE (nombre);


--
-- Name: nutricionista nutricionista_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.nutricionista
    ADD CONSTRAINT nutricionista_pkey PRIMARY KEY (rut);


--
-- Name: recetas recetas_idnutricionista_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.recetas
    ADD CONSTRAINT recetas_idnutricionista_key UNIQUE (idnutricionista);


--
-- Name: recetas recetas_idusuario_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.recetas
    ADD CONSTRAINT recetas_idusuario_key UNIQUE (idusuario);


--
-- Name: recetas recetas_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.recetas
    ADD CONSTRAINT recetas_pkey PRIMARY KEY (idreceta);


--
-- Name: usuario usuario_id_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.usuario
    ADD CONSTRAINT usuario_id_key UNIQUE (idusuario);


--
-- Name: videos videos_idnutricionista_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.videos
    ADD CONSTRAINT videos_idnutricionista_key UNIQUE (idnutricionista);


--
-- Name: videos videos_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.videos
    ADD CONSTRAINT videos_pkey PRIMARY KEY (idvideos);


--
-- PostgreSQL database dump complete
--

